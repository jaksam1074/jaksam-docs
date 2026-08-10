---
title: "Vehicle window broken"
description: "Triggered server side when a player breaks a vehicle window."
icon: "car-burst"
---

```lua Event
RegisterNetEvent("vehicles_keys:vehicleWindowBroken", function(playerId, vehicleNetId)

end)
```

### Parameters

| Name           | Data Type | Description                              |
| -------------- | --------- | -------------------------------------------- |
| `playerId`     | integer   | The player server ID who broke the window       |
| `vehicleNetId` | integer   | The vehicle network ID                             |

## Example

```lua
RegisterNetEvent("vehicles_keys:vehicleWindowBroken", function(playerId, vehicleNetId)
    local vehicle = NetworkGetEntityFromNetworkId(vehicleNetId)

    print(GetPlayerName(playerId) .. " broke the window of plate " .. GetVehicleNumberPlateText(vehicle))
end)
```
