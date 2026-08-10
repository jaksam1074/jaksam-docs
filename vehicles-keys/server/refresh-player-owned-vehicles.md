---
title: "Refresh player owned vehicles"
description: "Refresh a player's owned vehicles list server side, for example after a purchase."
icon: "rotate"
---

Using this export (from server side) will refresh the list of the player's owned vehicles (from `owned_vehicles` on ESX or `player_vehicles` on QBCore).

```lua Export
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId, instantly)
```

### Parameters

| Name        | Data Type | Description                                                                                                                    |
| ----------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `playerId`  | integer   | The player server ID                                                                                                                  |
| `instantly` | boolean   | Optional. By default, it waits 2 seconds before refreshing. If you know for sure you need it instantly, pass `true`, otherwise it can be omitted. |

### Example

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    -- This will refresh the player's owned vehicles after they buy a vehicle (just an example)

    exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId)
end)
```
