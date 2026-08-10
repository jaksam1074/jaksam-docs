---
title: "Vehicle parked"
description: "Triggered after a vehicle from the owned vehicles garage has been parked."
icon: "square-parking"
---

Triggered after the vehicle from the owned vehicles garage has been parked.

```lua Event
AddEventHandler("jobs_creator:garage_owned:vehicleParked", function(vehicleModel, vehiclePlate)
end)
```

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `vehicleModel` | integer | The vehicle's entity model |
| `vehiclePlate` | string | Vehicle's plate |