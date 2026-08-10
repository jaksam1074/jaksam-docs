---
title: "On vehicle resell"
description: "Triggered server side after a player resells a vehicle to a dealership."
icon: "hand-holding-dollar"
---

This event is triggered after a player resells a vehicle to a dealership.

```lua Event
AddEventHandler("dealerships_creator:dealerships:onVehicleResell", function(dealershipId, plate, vehicleName, playerId, resellPrice)

end)
```

### Parameters

| Name           | Data Type | Description                                     |
| -------------- | --------- | ---------------------------------------------------- |
| `dealershipId` | integer   | The dealership ID where the vehicle was resold          |
| `plate`        | string    | The vehicle's plate                                     |
| `vehicleName`  | string    | The vehicle spawn name                                  |
| `playerId`     | integer   | Player server ID who resold the vehicle                  |
| `resellPrice`  | integer   | Amount of money the player received                       |
