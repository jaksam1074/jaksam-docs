---
title: "Get closest door"
description: "Get the closest active door to the player."
icon: "door-closed"
---

Returns the closest **active** door to the player.

```lua Export
exports["doors_creator"]:getClosestActiveDoor()
```

### Return

| Name       | Data Type | Description                                       |
| ---------- | --------- | ----------------------------------------------------- |
| `door`     | table     | Table containing `door.id` and `door.object`            |
| `distance` | float     | Distance from the door                                  |

## Example

```lua
Citizen.CreateThread(function()
    local closestDoor, closestDist = exports["doors_creator"]:getClosestActiveDoor()

    if(closestDoor and closestDist < 3.0) then
        print("The closest door is " .. closestDoor.id .. " and is " .. closestDist .. " meters away")
    end
end)
```
