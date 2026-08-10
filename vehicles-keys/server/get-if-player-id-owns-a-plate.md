---
title: "Get if player ID owns a plate"
description: "Check if a specific player owns a vehicle plate server side."
icon: "circle-question"
---

This export can be used to know if a player owns a vehicle plate (can also check shared, temporary, etc.).

```lua Export
exports["vehicles_keys"]:isPlayerOwnerOfVehiclePlate(playerId, plate, onlyOwnedVehicles)
```

### Parameters

| Name                 | Data Type | Description                                                                                     |
| --------------------- | --------- | ---------------------------------------------------------------------------------------------------- |
| `playerId`             | integer   | The player server ID                                                                                   |
| `plate`                | string    | The vehicle plate to check                                                                              |
| `onlyOwnedVehicles`    | boolean   | `true` = only search owned vehicles. `false` = also search temporary vehicles, shared keys, etc.         |

### Return

`true` if the vehicle is owned.

`false` if the vehicle is not owned.

## Example

```lua
RegisterCommand("checkPlate", function(playerId, args)
    local plate = args[1] -- Example "ABC 123"

    if(exports["vehicles_keys"]:isPlayerOwnerOfVehiclePlate(playerId, plate, false)) then
        print("I own this vehicle plate")
    else
        print("I DO NOT own this vehicle plate")
    end
end)
```
