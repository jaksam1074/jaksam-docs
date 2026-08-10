---
title: "Step completed"
description: "Triggered when a step of a heist is completed."
icon: "circle-check"
---

Triggered when a step of a heist is completed.

```lua Event
RegisterNetEvent("robberies_creator:heist:stepCompleted", function(playerId, heistId, stageId, stepType)

end)
```

### Parameters

| Name       | Data Type | Description                                                                              |
| ---------- | --------- | -------------------------------------------------------------------------------------------- |
| `playerId` | integer   | Player server ID who completed the step                                                       |
| `heistId`  | integer   | Heist ID                                                                                        |
| `stageId`  | integer   | Stage ID                                                                                        |
| `stepType` | string    | The step type. Available step types are listed [below](#step-types)                            |

### Step types

- `SAFE`
- `ROBBABLE_OBJECT`
- `HACKABLE_PANEL`
- `THERMAL_CHARGE`
- `LOCKPICKABLE_DOOR`

## Example

```lua
-- This hypothetical example will give xp when a player completes a step that has a minigame
RegisterNetEvent("robberies_creator:heist:stepCompleted", function(playerId, heistId, stageId, stepType)
    if(stepType ~= "ROBBABLE_OBJECT") then
        TriggerEvent("xp_script:addPlayerXp", playerId, 10)
    end
end)
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
