---
title: "On vehicle bought"
description: "Triggered when a player buys a vehicle from a buyable garage marker."
icon: "car"
---

Triggered when a player buys a vehicle from a buyable garage marker.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:permanent_garage:vehicleBought", function(playerId, markerId, vehicleName, vehicleId)
end)
```

```lua Example
RegisterNetEvent("jobs_creator:permanent_garage:vehicleBought", function(playerId, markerId, vehicleName, vehicleId)
    print("Player ID: " .. playerId .. " bought a " .. vehicleName .. " with ID " .. vehicleId .. " from marker " .. markerId)
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player's server ID |
| `markerId` | integer | Marker ID |
| `vehicleName` | string | Vehicle model name |
| `vehicleId` | integer | Vehicle ID in the database |