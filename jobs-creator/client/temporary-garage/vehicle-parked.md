---
title: "Vehicle parked"
description: "Triggered after a vehicle from the temporary garage has been parked."
icon: "square-parking"
---

Triggered after the vehicle from the temporary garage has been parked.

```lua Event
AddEventHandler("jobs_creator:temporary_garage:vehicleParked", function(vehicleModel, vehiclePlate)
end)
```

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `vehicleModel` | integer | The vehicle's entity model |
| `vehiclePlate` | string | Vehicle's plate |