---
title: "Vehicle parked"
description: "Triggered after a vehicle from the buyable vehicles garage has been parked."
icon: "car"
---

Triggered after the vehicle from the buyable vehicles garage has been parked.

```lua Event
AddEventHandler("jobs_creator:permanent_garage:vehicleParked", function(vehicleModel, vehiclePlate)
end)
```

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `vehicleModel` | integer | The vehicle's entity model |
| `vehiclePlate` | string | Vehicle's plate |