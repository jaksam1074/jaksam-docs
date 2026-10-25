---
title: "Editable files"
description: "Los archivos de Boosting Creator pensados para editarse: formato de matrícula, trabajos de policía, debug, nombres de events externos, garaje de QBCore y los hooks."
icon: "file-pen"
---

Casi todo Boosting Creator se configura en el juego. Unas pocas cosas están en la carpeta `integrations/`, porque son código o porque casi nunca cambian.

<Warning>
  Guarda una copia de estos archivos antes de actualizar el script: una actualización puede sustituirlos.
</Warning>

## integrations/sh_integrations.lua

| Valor | Qué hace |
| --- | --- |
| `EXAMPLE_PLATE` | Formato de las matrículas de los contratos. Las letras y los números son aleatorios, `#` marca la parte fija: `"#BST#123"` da `BST920`, `BST945`... Máximo 8 caracteres. |
| `POLICE_JOBS_NAMES` | Trabajos que cuentan como [policía](/es/boosting-creator/guides/police). |
| `SECONDS_TO_REFRESH_SHARED_OBJECT` | Actualiza el objeto del framework cada X segundos, `nil` para no actualizarlo nunca. |
| `DEBUG_OUTPUTS` | Líneas de debug en la consola del servidor y en F8. También `setr boosting_creator_debug 1` en el `server.cfg`, sin editar el archivo. Actívalo cuando pidas soporte. |

## integrations/sv_integrations.lua

| Valor | Qué hace |
| --- | --- |
| `EXTERNAL_EVENTS_NAMES` | Cámbialo solo si tu framework renombró sus events y el script no los encuentra. |
| `VIN_SCRATCH_QB_GARAGE` | Solo QBCore: el garaje en el que se guarda un auto con el VIN borrado, por defecto `pillboxgarage`. |
| `CanPlayerJoinBoostingQueue` | [Hook](/es/boosting-creator/server#canplayerjoinboostingqueue) para dejar a un jugador fuera de la cola. |
| `OnBoostingContractEnded` | [Hook](/es/boosting-creator/server#onboostingcontractended) que se llama cuando termina un contrato. |

## integrations/cl_integrations.lua

| Valor | Qué hace |
| --- | --- |
| `DEFAULT_PROGRESSBAR_COLOR` | Color de la progress bar por defecto, un código hex. |
| `BLIP_TIME_AFTER_POLICE_ALERT` | Segundos que el blip de aviso del módulo de dispatch `default` se queda en el mapa, por defecto 120. |
| `EXTERNAL_SCRIPTS_NAMES` | Nombres de las carpetas de `datacrack`, `utk_fingerprint` y `ultra-keypackhack`, si los renombraste. |

## current_config.json

Los ajustes del panel se guardan en `boosting_creator/current_config.json`. Edítalos desde el panel. Dos valores no tienen campo en él:

- `specificWebhooks`: un webhook de Discord por tipo de log, mira [Logs de Discord](/es/boosting-creator/guides/admin-panel#logs-de-discord)
- `minigamesMinSeconds`: el tiempo mínimo que puede durar un minijuego, mira [Minijuegos](/es/boosting-creator/guides/minigames#crear-tu-propio-minijuego)

Para el script antes de editar el archivo a mano, o el panel puede guardar encima de tu cambio.
