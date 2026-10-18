---
title: "Redadas"
description: "Deja que los trabajos de policía revienten talleres de falsificación, incauten pruebas y los precinten."
icon: "building-shield"
---

Los agentes revientan la puerta de un taller, lo registran y lo precintan. Las redadas se configuran en `Config.Raid` (`config/raid.lua`) o en la página de redadas de `/documents config`. `Config.Raid.enabled = false` las desactiva.

## Cuerpos

Uno o más trabajos que hacen redadas juntos, desde un rango que eliges, con un armario de pruebas en un lugar que eliges:

```lua
forces = {
    police = { label = 'LSPD', jobs = { 'police' }, minGrade = 0, locker = vec4(452.3, -980.0, 30.69, 90.0) },
},
```

<Warning>
  Coloca el armario de pruebas de cada cuerpo en el juego (página de redadas de `/documents config`). **Sin armario no se puede incautar nada.**
</Warning>

## Cómo va una redada

<Steps>
  <Step title="Reventar la puerta">
    En la puerta de un taller que tiene dueño. Hacen falta suficientes agentes de servicio conectados (`minOfficers`), el item `door_ram` (`item`, `''` para ninguno) y tiempo: el tiempo de asalto del nivel de seguridad del taller (30 segundos, 90 con la mejora). El agente se queda en la puerta: alejarse o cancelar lo detiene.
  </Step>
  <Step title="El aviso">
    Con un guardia de seguridad contratado, todos los de dentro reciben el aviso y ven la cuenta atrás. Sin guardia, nadie de dentro se entera. Con la mejora de seguridad, los miembros que están fuera reciben una alarma.
  </Step>
  <Step title="Destruir pruebas">
    Los miembros avisados destruyen pruebas en las cuatro trituradoras durante la cuenta atrás: todos los pedidos abiertos, o lo que hay en un almacén. Los trabajadores también: en la página Personal del portátil el jefe elige qué destruyen cuando el guardia da la alarma, y se reparten las tareas. Lo que no esté hecho cuando cede la puerta se queda.
  </Step>
  <Step title="La puerta abierta">
    La puerta queda abierta `openMinutes`. Los agentes entran, los trabajadores y el guardia levantan las manos, y ninguna estación, ordenador o portátil del taller acepta acciones. En cada estantería un agente vacía el almacén en el armario de pruebas del cuerpo. En el portátil del jefe se incauta el equipo (`equipmentLoss`).
  </Step>
  <Step title="Precintar">
    Un agente precinta el taller en su puerta, o se acaba el tiempo. A todos los de dentro se les pone en la puerta, y durante `sealHours` nadie del trabajo propietario puede entrar. Los trabajadores no hacen nada mientras tanto y no se les debe sueldo por ese tiempo.
  </Step>
</Steps>

Un taller se puede volver a asaltar `cooldownHours` después del último asalto. Un precinto termina solo. Un taller que pierde a su dueño pierde su precinto, y un reinicio en mitad de una redada deja el taller precintado.

## Configuración

```lua
Config.Raid = {
    enabled = true,
    minOfficers = 2,            -- officers of all forces that must be online (0 = no minimum)
    dutyOnly = true,            -- only officers on duty count and act
    item = 'door_ram',          -- the item a breach needs ('' = none)
    consumeItem = true,         -- the item is used up when the door gives way
    warnNeedsGuard = true,      -- those inside are warned only when the workshop has a security guard
    alarmNeedsSecurity = true,  -- members elsewhere are alarmed only with the security upgrade
    openMinutes = 20,           -- the door stays open this long unless sealed earlier
    sealHours = 12,             -- nobody of the owning job gets in for this long (0 = no seal)
    cooldownHours = 24,         -- no new breach for this long after a breach
    retryMinutes = 5,           -- a breach given up can be tried again after this long
    equipmentLoss = 'level',    -- 'level' one level down | 'all' gone | 'nothing' cannot be seized
    seizeSeconds = 10,
    shredWhile = 'breach',      -- 'breach' only during the countdown | 'raid' until the raid is over
    shredSeconds = 8,
    workersShred = true,
    locker = { slots = 200, weight = 2000.0 },
}
```

## Comandos de admin

| Comando | Qué hace |
| --- | --- |
| `/documents raid` | Lista las redadas y los precintos |
| `/documents raid <workshop> end` | Termina una redada en curso |
| `/documents raid <workshop> unseal` | Quita un precinto |
| `/documents raid <workshop> reset` | Además borra la espera hasta la siguiente redada |

## Dispatch y progress bar

- `Editable.CanRaid` y `Editable.OnRaid` en `editable/server.lua`: añade tus propias condiciones, o envía un aviso de dispatch. Mira [Can raid](/es/jaksam-identity/server/hooks/can-raid) y [On raid](/es/jaksam-identity/server/hooks/on-raid).
- `Editable.Progress` en `editable/client.lua`: sustituye la progress bar. Mira [Progress bar](/es/jaksam-identity/client/progress-bar).

El item `door_ram` está en los tres archivos de items de la carpeta install, su imagen en `install/images/`.
