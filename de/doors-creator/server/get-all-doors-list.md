---
title: "Liste aller Türen abrufen"
description: "Ruft server-seitig die Daten aller Türen ab."
icon: "list"
---

```lua Export
exports["doors_creator"]:getAllDoors()
```

### Rückgabe

Eine Table mit den Daten aller Türen.

## Beispiel

```lua
Citizen.CreateThread(function()
    local doors = exports["doors_creator"]:getAllDoors()

    for k, doorData in pairs(doors) do
        if(doorData.allowedJobs and doorData.allowedJobs["police"]) then
            print(doorData.id .. " is a police door")
        end
    end
end)
```
