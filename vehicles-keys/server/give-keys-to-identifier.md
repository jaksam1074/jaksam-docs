---
title: "Give keys to identifier"
description: "Give vehicle keys to a player identifier server side."
icon: "key"
---

```lua Export
exports["vehicles_keys"]:giveVehicleKeysToIdentifier(identifier, plate, type)
```

### Parameters

| Name         | Data Type         | Description                                                                                                  |
| ------------ | ------------------ | ------------------------------------------------------------------------------------------------------------- |
| `identifier` | string              | The target player identifier/license                                                                            |
| `plate`      | string              | The vehicle plate                                                                                               |
| `type`       | string (optional)  | The vehicle type. Defaults to `"temporary"`. Available types: `"temporary"`, `"owned"`, `"other_player"`          |

## Example

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    local identifier = xPlayer.identifier

    exports["vehicles_keys"]:giveVehicleKeysToIdentifier(identifier, plate, "owned")
end)
```
