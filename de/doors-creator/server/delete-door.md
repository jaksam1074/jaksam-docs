---
title: "Tür löschen"
description: "Entfernt server-seitig eine Tür anhand ihrer ID."
icon: "trash"
---

```lua Export
exports["doors_creator"]:deleteDoor(doorId)
```

### Parameter

| Name     | Datentyp | Beschreibung                     |
| -------- | --------- | ---------------------------------- |
| `doorId` | integer   | Die ID der zu entfernenden Tür         |

### Rückgabe

| Datentyp | Beschreibung                                      |
| --------- | ----------------------------------------------------- |
| boolean   | `true`, falls die Tür entfernt wurde, sonst `false`        |

## Beispiel

```lua
Citizen.CreateThread(function()
    local doorId = 55

    local success = exports["doors_creator"]:deleteDoor(doorId)

    if success then
        print("Door with ID " .. doorId .. " has been removed")
    else
        print("Failed to remove door with ID " .. doorId)
    end
end)
```
