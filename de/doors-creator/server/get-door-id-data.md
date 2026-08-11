---
title: "Tür-ID-Daten abrufen"
description: "Ruft die Daten einer Tür server-seitig anhand ihrer ID ab."
icon: "door-closed"
---

```lua Export
exports["doors_creator"]:getDoorIdData(doorId)
```

### Parameter

| Name     | Datentyp | Beschreibung                   |
| -------- | --------- | -------------------------------- |
| `doorId` | integer   | Die Tür-ID, für die die Daten abgerufen werden sollen    |

## Beispiel

```lua
Citizen.CreateThread(function()
    local doorId = 55
    local doorData = exports["doors_creator"]:getDoorIdData(doorId)

    print("The name of door " .. doorId .. " is " .. doorData.label)
end)
```
