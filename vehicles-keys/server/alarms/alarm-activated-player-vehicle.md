---
title: "Alarm activated (player vehicle)"
description: "Triggered server side when an alarm is activated on a player vehicle."
icon: "car"
---

Triggered when an alarm on a player vehicle is activated.

```lua Event
RegisterNetEvent("vehicles_keys:alarmOnPlayerVehicle", function(vehicle, vehicleCoords, alarmLevel)

end)
```

### Parameters

| Name            | Data Type | Description                       |
| --------------- | --------- | -------------------------------------- |
| `vehicle`       | integer   | Vehicle handle                            |
| `vehicleCoords` | vector3   | The coordinates of the vehicle              |
| `alarmLevel`    | integer   | The level of the installed alarm             |

## Example

```lua
RegisterNetEvent("vehicles_keys:alarmOnPlayerVehicle", function(vehicle, vehicleCoords, alarmLevel)
    -- You can add an external notification if you want
end)
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
