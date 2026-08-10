---
title: "Get all buildings list"
description: "Get the data of all buildings server side."
icon: "list"
---

```lua Export
exports["doors_creator"]:getAllBuildings()
```

### Return

A table with all buildings' data.

## Example

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
