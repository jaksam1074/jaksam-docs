---
title: "Give keys to player ID"
description: "Give vehicle keys to an online player server side."
icon: "key"
---

```lua Export
exports["vehicles_keys"]:giveVehicleKeysToPlayerId(playerId, plate, type)
```

### Parameters

| Name       | Data Type         | Description                                                                                                  |
| ---------- | ------------------ | ------------------------------------------------------------------------------------------------------------- |
| `playerId` | integer             | The target player server ID                                                                                     |
| `plate`    | string              | The vehicle plate                                                                                               |
| `type`     | string (optional)  | The vehicle type. Defaults to `"temporary"`. Available types: `"temporary"`, `"owned"`, `"other_player"`          |

## Example

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    exports["vehicles_keys"]:giveVehicleKeysToPlayerId(playerId, plate, "owned")
end)
```
