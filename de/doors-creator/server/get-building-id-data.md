---
title: "Gebäude-ID-Daten abrufen"
description: "Ruft die Daten eines Gebäudes server-seitig anhand seiner ID ab."
icon: "building"
---

```lua Export
exports["doors_creator"]:getBuildingIdData(buildingId)
```

### Parameter

| Name         | Datentyp | Beschreibung                       |
| ------------ | --------- | ------------------------------------ |
| `buildingId` | integer   | Die Gebäude-ID, für die die Daten abgerufen werden sollen    |

## Beispiel

```lua
Citizen.CreateThread(function()
    local buildingId = 55
    local buildingData = exports["doors_creator"]:getBuildingIdData(buildingId)

    print("The name of building " .. buildingId .. " is " .. buildingData.label)
end)
```
