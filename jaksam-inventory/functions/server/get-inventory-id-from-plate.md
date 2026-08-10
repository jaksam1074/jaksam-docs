---
title: "Get inventory ID from plate"
description: "Resolves the full inventory ID for a vehicle compartment using only the vehicle plate."
icon: "id-card"
---

Resolves the full inventory ID for a vehicle compartment using only the vehicle plate.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getInventoryIdFromPlate(plate, compartment)
```

```lua Example
-- Get trunk inventory ID
local plate = GetVehicleNumberPlateText(vehicle)
local trunkId = exports['jaksam_inventory']:getInventoryIdFromPlate(plate, "trunk")

if trunkId then
    print("Trunk ID: " .. trunkId)
    -- Now you can use standard inventory functions
    local inventory = exports['jaksam_inventory']:getInventory(trunkId)
end

-- Get glovebox inventory ID
local gloveboxId = exports['jaksam_inventory']:getInventoryIdFromPlate("ABC 123", "glovebox")
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `plate` | string | The vehicle license plate |
| `compartment` | string | Either "trunk" or "glovebox" |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| nil | The full inventory ID (format: `"vehicle:plate:model:compartment"`), nil if vehicle not found |

### Notes

Searches in this order:

1. Owned vehicles database (ESX: `owned_vehicles`, QBCore: `player_vehicles`)
2. Existing inventories in the `jaksam_inventory` table
3. Currently spawned vehicles (`GetAllVehicles` - NPC vehicles)

For owned vehicles, automatically creates inventory if it doesn't exist. Created inventories are persistent for owned vehicles, temporary for NPC vehicles. Works even if the vehicle is not currently spawned (garage).
