---
title: "Get vehicle inventory limits"
description: "Returns the trunk or glovebox limits for a vehicle based on model."
icon: "car"
---

Returns the trunk or glovebox limits for a vehicle based on model. Uses the configuration from `_data/vehicles.lua` with priority: `trunkByModel`/`gloveboxByModel` > `trunkByClass`/`gloveboxByClass`. Returns `0, 0` if the vehicle/class is configured to not have trunk/glovebox (`noTrunkVehicles`, `noTrunkClasses`, etc.)

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getVehicleInventoryLimits(vehicleModel, inventoryType)
```

```lua Example
local vehicle = GetVehiclePedIsIn(PlayerPedId(), false)
local maxSlots, maxWeight = exports['jaksam_inventory']:getVehicleInventoryLimits(GetEntityModel(vehicle), "trunk")

if maxWeight then
    print("Trunk max weight: " .. maxWeight)
else
    print("No specific config for this vehicle model/class")
end

-- Get glovebox limits for 'adder' vehicle
local gloveboxSlots, gloveboxWeight = exports['jaksam_inventory']:getVehicleInventoryLimits('adder', "glovebox")
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `vehicleModel` | number \| string | The vehicle model hash (from `GetEntityModel`) or the model name as string |
| `inventoryType` | string | Either `"trunk"` or `"glovebox"` |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `maxSlots` | number \| nil | The maximum slots for the vehicle inventory, or nil if no config found |
| `maxWeight` | number \| nil | The maximum weight for the vehicle inventory, or nil if no config found |

### Notes

The source docs noted a missing comma between `'adder'` and `"glovebox"` in the original example, corrected here. Worth double-checking whether that was also a bug in the underlying script itself.
