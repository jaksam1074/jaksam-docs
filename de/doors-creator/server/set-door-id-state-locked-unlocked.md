---
title: "Tür-ID-Status setzen (verriegelt/entriegelt)"
description: "Verriegle oder entriegle eine Tür server-seitig anhand ihrer ID."
icon: "lock"
---

```lua Export
exports["doors_creator"]:setDoorState(doorId, state)
```

### Parameter

| Name     | Datentyp | Beschreibung                               |
| -------- | --------- | ---------------------------------------------- |
| `doorId` | integer   | Die Tür-ID                                       |
| `state`  | integer   | Der neue Status der Tür. 1 = verriegelt, 0 = entriegelt      |

## Beispiel

```lua
Citizen.CreateThread(function()
    local doors = exports["doors_creator"]:getAllDoors()

    -- Dies schließt ALLE Türen
    for k, doorData in pairs(doors) do
        exports["doors_creator"]:setDoorState(doorData.id, 1)
    end
end)
```
