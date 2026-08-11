---
title: "Liste aller Gebäude abrufen"
description: "Ruft server-seitig die Daten aller Gebäude ab."
icon: "list"
---

```lua Export
exports["doors_creator"]:getAllBuildings()
```

### Rückgabe

Eine Table mit den Daten aller Gebäude.

## Beispiel

```lua
Citizen.CreateThread(function()
    local buildings = exports["doors_creator"]:getAllBuildings()

    for k, buildingData in pairs(buildings) do
        if(buildingData.allowedJobs and buildingData.allowedJobs["police"]) then
            print(buildingData.label .. " is a police building")
        end
    end
end)
```
