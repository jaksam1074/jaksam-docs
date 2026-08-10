---
title: "Get door ID data"
description: "Get a door's data server side by its ID."
icon: "door-closed"
---

```lua Export
exports["doors_creator"]:getDoorIdData(doorId)
```

### Parameters

| Name     | Data Type | Description                   |
| -------- | --------- | -------------------------------- |
| `doorId` | integer   | The door ID to get the data for    |

## Example

```lua
Citizen.CreateThread(function()
    local doorId = 55
    local doorData = exports["doors_creator"]:getDoorIdData(doorId)

    print("The name of door " .. doorId .. " is " .. doorData.label)
end)
```
