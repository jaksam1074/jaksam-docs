---
title: "Talleres de falsificación"
description: "Añade talleres de falsificación, deja que los trabajos los compren y vendan, y configura mejoras, almacenes y quién puede entrar."
icon: "warehouse"
---

Un taller es una puerta en algún lugar del mundo que lleva a su propia copia de la sala de falsificación (el interior de DNI falsos de los bikers de `bob74_ipl`). Pertenece a un trabajo o a nadie.

<Warning>
  **De serie no hay ningún taller configurado.** Todo el lado de la falsificación queda invisible hasta que añadas uno en `config/forgery.lua` o en el juego con `/documents config`.
</Warning>

## Añadir un taller

En `Config.Forgery.workshops` (`config/forgery.lua`):

```lua
workshops = {
    docks = { label = 'Docks', entrance = vec4(0.0, 0.0, 0.0, 0.0), price = 150000, jobs = {}, minGrade = 0 },
    east_side = { label = 'East side', entrance = vec4(0.0, 0.0, 0.0, 0.0), price = 90000, jobs = { 'vagos', 'ballas' }, minGrade = 1 },
},
```

| Campo | Descripción |
| --- | --- |
| `label` | Nombre del taller |
| `entrance` | La puerta exterior, un `vec4` con la orientación para salir |
| `price` | Lo que paga un trabajo para comprarlo |
| `jobs` | Los trabajos que pueden tenerlo, `{}` para todos |
| `minGrade` | Rango más bajo del trabajo propietario que puede entrar |
| `owner` | Opcional: el trabajo al que pertenece desde el primer arranque |

<Tip>
  En el juego es más fácil: en la página de talleres de `/documents config` pulsa **Place**, ve a la puerta y haz clic. Los admins también añaden y quitan talleres ahí con el servidor en marcha, y dan un taller a un trabajo o se lo quitan.
</Tip>

## Comprar y tener

- **Comprar:** un taller sin dueño muestra "Workshop for sale" en su puerta. El jefe de un trabajo lo compra para el trabajo con dinero negro (`Config.Forgery.payAccount`).
- **Varios por trabajo:** un trabajo puede tener tantos como pueda pagar, o tantos como permita `ownership.perJob`.
- **Quién es el jefe:** el rango más alto del trabajo propietario, y tantos rangos por debajo como diga `ownership.bossDepth`. El jefe compra, vende, contrata y mejora.
- **Los miembros** del trabajo propietario entran desde el `minGrade` del taller. Los demás llaman al timbre, y un miembro de dentro puede dejarles pasar.
- **Vender:** el jefe lo vende en el portátil del taller (página Upgrades) y recupera `ownership.refund` de lo que se pagó (nada por un taller que dio un admin). `ownership.sellable = false` lo desactiva.

```lua
ownership = {
    perJob = 0,           -- workshops one job may own (0 = as many as it can pay)
    bossDepth = 0,        -- ranks below a job's highest that may buy, sell and manage too
    sellable = true,      -- the boss may sell the workshop at its laptop
    refund = 0.5,         -- share of what was paid that comes back when it is sold
    onRelease = 'room',   -- what stays when a workshop loses its owner
},
```

### Qué queda cuando un taller pierde a su dueño

| `onRelease` | Resultado |
| --- | --- |
| `room` | Las mejoras y los almacenes se quedan, los trabajadores se despiden y los pedidos abiertos se descartan |
| `all` | Todo se queda para el siguiente dueño |
| `nothing` | Una sala vacía |

<Info>
  **Dinero negro:** en ESX la cuenta `black_money`, en QBCore el item `markedbills` (su valor en `metadata.worth`), en Qbox el item apilable `black_money`.
</Info>

## Mejoras

El jefe compra mejoras en el portátil, con dinero negro.

| Mejora | Qué cambia |
| --- | --- |
| **Equipo** | La calidad máxima que puede alcanzar una falsificación hecha aquí (ninguno, básico hasta 70, pro hasta 100), cuántos trabajadores caben y la máquina de relieve (solo pro) |
| **Seguridad** | Cuánto tardan los agentes en reventar la puerta (30 segundos, 90 con la mejora), y una alarma a los miembros que están fuera durante una redada |
| **Estilo** | El aspecto del interior |

Los precios están en `Config.Forgery.upgrades`, o en el juego.

## El portátil del jefe

El portátil de la mesa del jefe muestra su página en la pantalla real de la sala, con pestañas:

- **Resumen:** trabajadores, dispositivos y mesas
- **Personal:** contratar y despedir trabajadores y al guardia, pagar sueldos, elegir qué destruyen los trabajadores durante una redada
- **Tickets:** la cola de pedidos
- **Material:** pedir material, entregado en el almacén de materias primas tras un tiempo
- **Upgrades:** comprar mejoras, vender el taller

## Almacenes

Cada taller tiene tres almacenes que se abren en sus estanterías:

| Almacén | Contenido |
| --- | --- |
| Materias primas | Tarjetas en blanco, tóner y todo lo que necesita la falsificación |
| Libre | Libre para los jugadores |
| Resultados | Donde los trabajadores dejan los documentos terminados |

Los tamaños están en `Config.Forging.stores`. Los trabajadores meten los documentos de un pedido en un **montón de ID** (`id_stack`), un contenedor que los guarda en un solo slot. Arrastrar un documento sobre otro también hace un montón. qb-inventory no tiene contenedores, así que ahí los documentos llegan uno a uno.

<Note>
  Cada target llega a 2 metros (`Config.TargetDistance`), y el servidor solo acepta acciones de un miembro que esté en la estación. Los invitados y los agentes que estén dentro no ven ninguna estación.
</Note>
