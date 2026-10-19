---
title: "Documentos y registro"
description: "Cómo funcionan los documentos, las clases de licencia, el registro y las tarjetas falsas en Jaksam Identity, y cómo añadir tus propios tipos de documento."
icon: "id-card"
---

## Cómo funciona

<CardGroup cols={2}>
  <Card title="El documento es la identidad" icon="id-card">
    Una consulta devuelve la identidad impresa en el documento. El script nunca comprueba quién lo lleva: un documento real robado funciona hasta que su dueño lo denuncia.
  </Card>

  <Card title="Solo el servidor sabe qué es real" icon="server">
    Los números reales están en el registro (`jksm_identity_documents`), los falsos en `jksm_identity_forgeries` con su calidad. Un item real y uno falso llevan exactamente los mismos metadatos.
  </Card>

  <Card title="Hechos, no fuerza" icon="scale-balanced">
    La caducidad, las suspensiones y las fotos antiguas se muestran en la tarjeta y en la consulta del registro. Nada se quita, bloquea o renueva automáticamente: lo que sigue es roleplay.
  </Card>

  <Card title="El framework guarda las licencias" icon="list-check">
    ESX: las tablas de esx_license (`licenses`, `user_licenses`). QBCore/Qbox: los metadatos del personaje `licences`.
  </Card>
</CardGroup>

<Note>
  **Anonimato:** la foto se hace a un clon local, no sincronizado, del personaje, sin máscara, sombrero ni gafas. Nadie cerca ve la cara, y la foto no muestra ninguna máscara.
</Note>

## Tipos de documento

Los tipos de documento se configuran en `Config.Documents` (`config/documents.lua`). Hay tres clases:

| Clase | Válido en el registro cuando | Ejemplo |
| --- | --- | --- |
| `identity` | el estado del registro es válido | DNI |
| `license` | el estado es válido **y** la licencia (o al menos una de sus clases) se sigue teniendo | Carné de conducir (clases A, B, C), permiso de armas |
| `badge` | el estado es válido **y** el dueño sigue en el trabajo | LSPD, LSMD, LSC |

Cada entrada tiene estos campos:

| Campo | Descripción |
| --- | --- |
| `item` | El nombre del item del inventario (el item debe existir en tu inventario) |
| `kind` | `identity`, `license` o `badge` |
| `license` | (solo `license`) el tipo de licencia: ESX la tabla `licenses`, QBCore/Qbox la clave en los metadatos `licences` |
| `licenses` | (solo `license`, en lugar de `license`) un documento para varios tipos de licencia, cada uno una clase |
| `job` | (solo `badge`) el trabajo al que pertenece la placa |
| `validityDays` | Días hasta que caduca, `nil` para nunca |
| `layout` | `id` (horizontal, por defecto) o `badge` (identificación de servicio vertical) |
| `theme` | Aspecto de la tarjeta: cabecera, título, colores. Las placas tienen además `word`, `emblem` (`star`, `shield`, `starOfLife`, `wrench`), `authority` y `authorityName` |

### Clases de licencia

Un documento puede cubrir varios tipos de licencia como clases:

```lua
drive = {
    item = 'driver_license',
    kind = 'license',
    licenses = { drive_bike = 'A', drive = 'B', drive_truck = 'C' },
    label = L('doc_driver'),
    validityDays = 180,
},
```

La tarjeta imprime las clases que se tenían al expedirla. La consulta del registro muestra las clases que se tienen ahora y nombra cada clase impresa que se ha retirado.

### Crear tu propio documento

Cualquier licencia de tu framework puede ser un documento. Añade el item a tu inventario y luego una entrada aquí:

```lua
hunting = { item = 'hunting_license', kind = 'license', license = 'hunting', label = 'Hunting licence', validityDays = 120 },
```

La guía completa, con el item para cada inventario, el aspecto de la tarjeta, las oficinas y las placas, está en [Crear un documento propio](/es/jaksam-identity/guides/custom-documents).

### Metadatos del item

Todos los documentos llevan los mismos campos: `serial`, `firstname`, `lastname`, `dob`, `sex`, `issued`, `expires`, `photo`, y `classes` con clases de licencia. `photo` es solo un ID de foto: la imagen está en la tabla `jksm_identity_photos`.

## Estados del registro

Cada documento real tiene un estado en el registro:

| Estado | Significado |
| --- | --- |
| `valid` | Nada raro |
| `lost` / `stolen` | Denunciado por el dueño en una oficina ciudadana |
| `seized` | Retirado por una autoridad |
| `suspended` | Suspendido hasta un momento fijado, válido de nuevo después |
| `replaced` | Se ha expedido al dueño un documento más nuevo del mismo tipo |
| `revoked` | Retirado para siempre |

Un documento nuevo siempre sustituye al anterior: el documento válido más antiguo de ese tipo se marca como `replaced`.

## La consulta del registro

La consulta del registro es lo que ve una autoridad. Informa de:

- **Sin registro:** el número es desconocido, y si existe alguna persona con el nombre impreso
- **Estado:** perdido, robado, retirado, suspendido, sustituido o revocado
- **Caducado:** la fecha de caducidad ha pasado
- **Falta la licencia / clase retirada:** la licencia, o una de las clases impresas, ya no se tiene
- **Dejó el trabajo:** el dueño de la placa ya no tiene ese trabajo
- **Datos que no coinciden:** el nombre o la fecha de nacimiento impresos no coinciden con el registro

Nunca revela quién hizo una falsificación ni su calidad. Los admins lo ven con `/documents truth <serial>`.

## Usar y mostrar un documento

`Config.UseAction` decide qué hace usar un item de documento:

| Valor | Comportamiento |
| --- | --- |
| `auto` | Lo muestra al jugador más cercano dentro de `Config.ShowDistance`, lo mira si no hay nadie |
| `view` | Siempre lo mira |
| `show` | Siempre lo muestra |
| `menu` | Pregunta cada vez |

Los documentos solo se muestran a jugadores en la misma instancia. **Mostrado de lejos solo se ven los fallos gruesos**, en la mano lo ves de cerca.

## Documentos falsos y fallos

Una tarjeta falsa muestra fallos en tres niveles. Cuántos depende de su calidad:

| Nivel | Ejemplos |
| --- | --- |
| A simple vista | Sello desplazado, fuente equivocada, color raro |
| En la mano | Foto borrosa, texto desalineado, falta la microimpresión, holograma plano |
| Bajo UV | Falta la marca UV |

El nivel UV aparece mientras quien mira lleva el item de lámpara UV (`Config.UvItem`, por defecto `uv_lamp`). Una buena falsificación puede pasar todas las comprobaciones visuales y fallar solo en el registro.

<Info>
  Un documento creado por una tienda de jaksam o una entrega de admin está **registrado** (real), salvo que su `rarity` de jaksam esté en `Config.UnregisteredRarities`. Entonces es una falsificación no registrada con la calidad `Config.UnregisteredQuality`.
</Info>
