---
title: "Alarm activated (NPC vehicle)"
description: "Triggered server side when an alarm is activated on an NPC vehicle."
icon: "car-side"
---

Triggered when an alarm is triggered on an NPC vehicle.

```lua Event
RegisterNetEvent("vehicles_keys:alarmOnNPCVehicle", function(vehicle, vehicleCoords)

end)
```

### Parameters

| Name            | Data Type | Description                     |
| --------------- | --------- | ------------------------------------ |
| `vehicle`       | integer   | Vehicle handle                          |
| `vehicleCoords` | vector3   | The coordinates of the vehicle            |

## Example

```lua
RegisterNetEvent("vehicles_keys:alarmOnNPCVehicle", function(vehicle, vehicleCoords)
    -- You can add an external notification if you want
end)
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
