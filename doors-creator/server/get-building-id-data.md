---
title: "Get building ID data"
description: "Get a building's data server side by its ID."
icon: "building"
---

```lua Export
exports["doors_creator"]:getBuildingIdData(buildingId)
```

### Parameters

| Name         | Data Type | Description                       |
| ------------ | --------- | ------------------------------------ |
| `buildingId` | integer   | The building ID to get the data for    |

## Example

```lua
Citizen.CreateThread(function()
    local buildingId = 55
    local buildingData = exports["doors_creator"]:getBuildingIdData(buildingId)

    print("The name of building " .. buildingId .. " is " .. buildingData.label)
end)
```
