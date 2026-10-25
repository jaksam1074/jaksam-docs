---
title: "Server"
description: "Server-side hooks and exports of Boosting Creator: keep players out of the queue, react when a contract ends, disable a script event."
icon: "server"
---

## Hooks

Both hooks are in `integrations/sv_integrations.lua`. Write your code inside the functions.

### CanPlayerJoinBoostingQueue

Called when a player presses **Join queue**. Return `false` to keep them out, for example for a gang check or a cooldown of yours.

```lua
function CanPlayerJoinBoostingQueue(playerId)
    return true
end
```

| Parameter | Type | Description |
| --- | --- | --- |
| `playerId` | `number` | Server id of the player |

Police jobs are refused before this hook is called.

### OnBoostingContractEnded

Called once when a contract ends, however it ends.

```lua
function OnBoostingContractEnded(playerId, contract, outcome, payout)
    if outcome == "delivered" then
        -- give an achievement, a bonus item...
    end
end
```

| Parameter | Type | Description |
| --- | --- | --- |
| `playerId` | `number` | Server id of the player who accepted the contract (the crew leader) |
| `contract` | `table` | The contract: `contract.model`, `contract.plate`, `contract.type` (`dropoff`, `vin`, `chop`, `bulk`), `contract.class.id`, `contract.class.label`, `contract.members` (every member, with `id` and `name`) |
| `outcome` | `string` | `delivered`, `vin_done`, `stored` (kept in the thief's garage), `failed`, `expired` or `cancelled` |
| `payout` | `number` | The money each member received (with a crew, one member's share), `0` when it paid nothing |

## Exports

### disableScriptEvent

Turns off one of the script's own event handlers, to replace it with yours.

```lua
exports["boosting_creator"]:disableScriptEvent(eventName)
```

| Parameter | Type | Description |
| --- | --- | --- |
| `eventName` | `string` | Name of the event to disable |

## vehicles_keys

When `vehicles_keys` is started, Boosting Creator uses its lockpick and hotwire instead of its own break-in and hotwire. Nothing to configure.
