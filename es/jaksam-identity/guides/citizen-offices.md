---
title: "Oficinas ciudadanas"
description: "Documentos iniciales, oficinas ciudadanas con un NPC en el mostrador, tasas y la integración con esx_dmvschool."
icon: "building-columns"
---

## Documentos iniciales

Todo personaje que nunca tuvo un documento de los tipos de la lista recibe uno tras cargar, en cuanto tiene nombre y fecha de nacimiento.

```lua
Config.Starter = {
    documents = { 'id_card' },
    delaySeconds = 15,          -- after the character has loaded
}
```

Los documentos iniciales **no tienen foto**: la foto se hace en la oficina con una renovación. Pon `documents = {}` para desactivarlo.

## Oficinas ciudadanas

Una oficina es un NPC en un mostrador, con un blip en el mapa. Cada oficina gestiona los tipos de documento de su lista. Los jugadores pueden:

- **Solicitar** un primer documento
- **Renovarlo**: mismo número, nueva caducidad y foto (hay que llevar el documento)
- **Pedir un duplicado** si se perdió o lo robaron: número nuevo, el anterior deja de ser válido
- **Denunciar** un documento perdido o robado, o **avisar de que apareció**
- **Entregar** sus propias tarjetas que ya no son válidas
- **Añadir una clase** conseguida después de imprimir la tarjeta (hace una renovación)

La foto se hace en el mostrador. Un documento suspendido, revocado o retirado bloquea el mostrador para ese tipo. **Aquí nunca se expiden placas**: salen de `/documents issue` o del export `Issue`, ver [Crear un documento propio](/es/jaksam-identity/guides/custom-documents).

<Note>
  Una tarjeta que no es del jugador recibe la misma respuesta tanto si es de otra persona como si es falsa, así que la oficina no sirve para probar falsificaciones.
</Note>

### Configuración

Las oficinas se configuran en `Config.Offices` (`config/office.lua`), o se colocan en el juego en la página de oficinas de `/documents config`.

```lua
Config.Offices = {
    payAccount = 'money',       -- 'money' (cash) | 'bank'
    pedDistance = 40.0,         -- a counter NPC exists only while the player is this close (metres)
    fees = {                    -- per document type; 0 = free
        id_card = { first = 100, renew = 50, replace = 150 },
        drive = { first = 250, renew = 100, replace = 300 },
        weapon = { first = 1000, renew = 400, replace = 1200 },
    },
    locations = {
        { label = L('office_city_hall'), coords = vec4(-517.63, -251.57, 35.67, 207.0), model = 'a_f_y_business_01',
          documents = { 'id_card', 'drive' }, blip = { sprite = 498, color = 0, scale = 0.7 } },
    },
}
```

Las tasas se cobran solo después de que la foto y la expedición salgan bien.

<Tip>
  Puedes abrir una oficina por autoridad, por ejemplo un mostrador de tráfico que solo gestiona `drive` y uno de policía que solo gestiona `weapon`.
</Tip>

## esx_dmvschool (solo ESX)

esx_dmvschool da la licencia tras aprobar el examen, pero no entrega tarjeta. Con `Config.DmvSchool` activo:

- el **primer carné de conducir se expide justo después del examen**, con una foto hecha allí y sin tasa (la autoescuela ya cobró)
- una clase aprobada más tarde **se imprime en el carné que lleva el jugador** (mismo número, caducidad y foto)
- sin la tarjeta encima, se avisa al jugador de que vaya a la oficina, que la añade

```lua
Config.DmvSchool = {
    enabled = true,
    document = 'drive',         -- the document type its licences are classes of
}
```

<Warning>
  esx_dmvschool no comprueba en el servidor el evento `esx_dmvschool:addLicense`, así que un cliente tramposo puede darse cualquier licencia con él. Protege el evento en esx_dmvschool, o pon `Config.DmvSchool.enabled = false`, en un servidor en producción.
</Warning>

## Ayuntamiento de QBCore y Qbox

En la versión QBCore, lo que entregan qb-core, qbx_core y qb-cityhall / qbx_cityhall se convierte en un documento registrado del personaje. qbx_cityhall lo expide con una foto hecha allí. En Qbox, quita `qbx_idcard`: Jaksam Identity responde en su lugar.
