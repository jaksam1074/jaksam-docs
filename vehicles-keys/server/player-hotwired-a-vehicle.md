---
title: "Player hotwired a vehicle"
description: "Triggered server side when a vehicle is hotwired."
icon: "bolt"
---

Triggered when a vehicle has been hotwired.

```lua Event
RegisterNetEvent("vehicles_keys:playerHotwiredVehicle", function(playerId, vehicleNetId)

end)
```

### Parameters

| Name           | Data Type | Description         |
| -------------- | --------- | ---------------------- |
| `playerId`     | integer   | Player server ID          |
| `vehicleNetId` | integer   | Vehicle network ID          |

## Example

```lua
RegisterNetEvent("vehicles_keys:playerHotwiredVehicle", function(playerId, vehicleNetId)
    local vehicle = NetworkGetEntityFromNetworkId(vehicleNetId)

    print("The player " .. GetPlayerName(playerId) .. " has just hotwired a vehicle with model " .. GetEntityModel(vehicle))
end)
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
