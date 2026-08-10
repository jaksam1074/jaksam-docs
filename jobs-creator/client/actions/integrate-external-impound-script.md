---
title: "Integrate external impound script"
description: "Hook your own impound script into Jobs Creator when a vehicle is impounded."
icon: "warehouse"
---

Triggered when a vehicle is impounded.

<CodeGroup>

```lua Event
AddEventHandler("jobs_creator:actions:vehicleImpounded", function(vehiclePlate, vehicleModel)
end)
```

```lua Example
RegisterNetEvent("jobs_creator:actions:vehicleImpounded", function(vehiclePlate, vehicleModel)
    -- You can add your impound script exports here
    TriggerServerEvent("impound_script:impoundVehicle", vehiclePlate, vehicleModel)
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `vehiclePlate` | string | The vehicle plate |
| `vehicleModel` | string | The vehicle model |