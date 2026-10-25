---
title: "Server"
description: "Hooks y exports del lado del servidor de Boosting Creator: deja a jugadores fuera de la cola, reacciona cuando termina un contrato y desactiva un event del script."
icon: "server"
---

## Hooks

Los dos hooks están en `integrations/sv_integrations.lua`. Escribe tu código dentro de las funciones.

### CanPlayerJoinBoostingQueue

Se llama cuando un jugador pulsa **Entrar en la cola**. Devuelve `false` para dejarlo fuera, por ejemplo para una comprobación de banda o un cooldown tuyo.

```lua
function CanPlayerJoinBoostingQueue(playerId)
    return true
end
```

| Parámetro | Tipo | Descripción |
| --- | --- | --- |
| `playerId` | `number` | Server id del jugador |

Los trabajos de policía se rechazan antes de que se llame a este hook.

### OnBoostingContractEnded

Se llama una vez cuando termina un contrato, termine como termine.

```lua
function OnBoostingContractEnded(playerId, contract, outcome, payout)
    if outcome == "delivered" then
        -- give an achievement, a bonus item...
    end
end
```

| Parámetro | Tipo | Descripción |
| --- | --- | --- |
| `playerId` | `number` | Server id del jugador que aceptó el contrato (el líder de la crew) |
| `contract` | `table` | El contrato: `contract.model`, `contract.plate`, `contract.type` (`dropoff`, `vin`, `chop`, `bulk`), `contract.class.id`, `contract.class.label`, `contract.members` (todos los miembros, con `id` y `name`) |
| `outcome` | `string` | `delivered`, `vin_done`, `stored` (guardado en el garaje del ladrón), `failed`, `expired` o `cancelled` |
| `payout` | `number` | El dinero que recibió cada miembro (con una crew, la parte de un miembro), `0` cuando no pagó nada |

## Exports

### disableScriptEvent

Desactiva uno de los event handlers propios del script, para sustituirlo por el tuyo.

```lua
exports["boosting_creator"]:disableScriptEvent(eventName)
```

| Parámetro | Tipo | Descripción |
| --- | --- | --- |
| `eventName` | `string` | Nombre del event que se desactiva |

## vehicles_keys

Cuando `vehicles_keys` está iniciado, Boosting Creator usa su ganzúa y su puente en lugar de su propio forzado y su propio puente. Nada que configurar.
