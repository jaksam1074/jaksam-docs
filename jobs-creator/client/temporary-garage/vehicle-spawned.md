---
title: "Vehicle spawned"
description: "Triggered after a temporary vehicle spawns."
icon: "car"
---

Triggered after the spawn of a temporary vehicle.

<CodeGroup>

```lua Event
AddEventHandler("jobs_creator:temporary_garage:vehicleSpawned", function(vehicle, vehicleName, vehiclePlate)
end)
```

```lua Example
AddEventHandler("jobs_creator:temporary_garage:vehicleSpawned", function(vehicle, vehicleName, vehiclePlate)
    -- Example to give keys to the vehicle (you may have a TriggerEvent to use, that's up to you)
    giveKeysToVehicle(vehicle)
    print(vehicleName) -- Example output 'adder'
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `vehicle` | vehicle handle | The vehicle's handle |
| `vehicleName` | string | The vehicle's name |
| `vehiclePlate` | string | Vehicle's plate |