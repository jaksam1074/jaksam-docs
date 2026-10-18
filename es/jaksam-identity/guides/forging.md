---
title: "Falsificación, trabajadores y pedidos"
description: "Cómo falsifican documentos a mano los jugadores, cómo se decide la calidad y cómo funcionan los trabajadores NPC y la cola de pedidos."
icon: "print"
---

## Falsificar a mano

Una falsificación pasa por las estaciones del taller, un ticket cada vez:

<Steps>
  <Step title="Foto">
    En el fondo: hazte una foto a ti o a otro jugador, o llama a un trabajador NPC con cámara. El equipo pro da un fondo de foto transparente.
  </Step>
  <Step title="Introducción de datos">
    En un ordenador o portátil: escribe el nombre, la fecha de nacimiento y los demás datos impresos.
  </Step>
  <Step title="Impresión">
    Usa una tarjeta en blanco y tóner de la impresora.
  </Step>
  <Step title="Plastificado">
    En una mesa de plastificado.
  </Step>
  <Step title="Relieve (opcional)">
    Solo con equipo pro, añade calidad.
  </Step>
  <Step title="Corte">
    En la cortadora: el documento está terminado.
  </Step>
</Steps>

Cada estación tiene un **skill check**: un acierto añade calidad, un fallo la quita (`Config.Forging.check`, y `Config.Forging.emboss` para la máquina de relieve). Puedes sustituir el minijuego, mira [Skill check](/es/jaksam-identity/client/skill-check).

### Copias

Un jugador puede copiar un documento que lleva encima. Los datos y la foto salen del original, y los campos se pueden cambiar: una base real con un nombre falso. La copia de una falsificación tiene como máximo la calidad del original menos `Config.Forging.copyLoss`.

### Calidad

La calidad de una falsificación (de 5 a 100) sale de:

- el **nivel del falsificador**: cada falsificación da experiencia, y el nivel fija la calidad base y qué se puede falsificar (primero identidades, luego licencias, luego placas)
- los skill checks de las estaciones
- un poco de suerte

Después la limitan el **equipo** del taller y la **tarjeta en blanco** usada (`doc_blank` hasta 60, `doc_blank_secure` hasta 100).

```lua
levels = {
    { xp = 0,    base = 35, kinds = { identity = true } },
    { xp = 150,  base = 45, kinds = { identity = true, license = true } },
    { xp = 500,  base = 58, kinds = { identity = true, license = true } },
    { xp = 1200, base = 70, kinds = { identity = true, license = true, badge = true } },
    { xp = 2500, base = 82, kinds = { identity = true, license = true, badge = true } },
},
```

La calidad decide qué fallos se ven a simple vista, en la mano, bajo UV o solo en el registro. Mira [Documentos falsos y fallos](/es/jaksam-identity/guides/documents-and-register#documentos-falsos-y-fallos).

### Material

| Item | Uso |
| --- | --- |
| `doc_blank` | Tarjeta en blanco, calidad hasta 60 |
| `doc_blank_secure` | Tarjeta de seguridad, calidad hasta 100 |
| `printer_toner` | Cartucho de tóner, `Config.Forging.tonerCharges` impresiones cada uno |
| `pvc_sheet` | Los trabajadores lo convierten en tarjetas en blanco |
| `holo_foil` | Los trabajadores lo convierten, con una tarjeta en blanco, en una tarjeta de seguridad |

El material se pide en un portátil con dinero negro y se entrega en el almacén de materias primas tras un tiempo (`Config.Forging.orders`).

## Pedidos

Un pedido es un número de tickets de un tipo de documento y tarjeta, de los que tiran los trabajadores y los jugadores (primero los urgentes, luego los más antiguos).

- **Prioridad:** baja, normal o urgente
- **Asignado a:** todos, un jugador o un trabajador
- **Pausar, reanudar, cancelar**
- **Datos fijos:** un pedido hecho desde una copia o un conjunto de datos lo repite en sus tickets
- **Lotes:** identidades inventadas sin foto, entregadas directamente a los trabajadores
- **Entregar:** un ticket se puede dar a los trabajadores, o a un trabajador, y recuperar

Cada acción necesita un rango mínimo en el trabajo:

```lua
queue = {
    maxAmount = 50,            -- tickets per order
    maxOpenTickets = 300,      -- open tickets per workshop
    offlineMinutes = 10,       -- an order assigned to a player who stays away this long goes back to everyone
    rights = { create = 0, priority = 1, assign = 2, pause = 1, cancel = 2, handover = 0 },
},
```

## Trabajadores NPC

El jefe contrata trabajadores en el portátil. Van de dispositivo en dispositivo, pasan los tickets por la impresora, la mesa de plastificado y la cortadora, recargan las impresoras con tóner y llevan los documentos terminados al almacén de resultados.

| Nivel | Calidad base | Velocidad | Probabilidad de fallo | Tickets a la vez |
| --- | --- | --- | --- | --- |
| Novato | 40 | 1.0 | 35% | 1 |
| Experto | 60 | 1.3 | 20% | 3 |
| Pro | 78 | 1.6 | 10% | 5 |

- **Roles:** falsificar, o producir material (PVC a tarjetas en blanco, tarjeta y lámina a tarjetas de seguridad)
- **Tarjetas de trabajador:** en un trabajador ves el nivel, un estado en directo con temporizador y barras de velocidad, tasa de fallo, tamaño de hoja y cartuchos. Da tareas directamente: traer tóner, coger un pedido o ticket, cambiar de rol, despedir
- **Sueldos:** el jefe ingresa dinero negro y los sueldos se descuentan una vez por periodo. Un trabajador sin pagar se va. El tiempo precintado tras una redada no cuesta nada
- **Guardia:** un guardia de seguridad por taller avisa a todos los de dentro cuando los agentes empiezan a reventar la puerta
- La calidad de un trabajador nunca supera la calidad base del mejor falsificador jugador del trabajo propietario
- El número de trabajadores depende de la mejora de equipo

Los precios de contratación, sueldos y tiempos de trabajo están en `config/npc.lua`, o en el juego en la página de trabajadores de `/documents config`.

<Tip>
  `Config.Bridge.menu = 'ox_lib'` sustituye las tarjetas de interacción de trabajadores y estaciones por menús contextuales de ox_lib.
</Tip>

## Modo demo

Para vídeos de presentación y servidores de demo: los almacenes siempre están llenos, los tiempos de trabajo son cortos, nada cuesta dinero y nadie falla. Actívalo con `Config.Demo = true` o `/documents demo on` (no se conserva tras un reinicio).
