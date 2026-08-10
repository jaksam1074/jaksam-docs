---
title: "Get all doors list"
description: "Get the data of all doors server side."
icon: "list"
---

```lua Export
exports["doors_creator"]:getAllDoors()
```

### Return

A table with all doors' data.

## Example

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
