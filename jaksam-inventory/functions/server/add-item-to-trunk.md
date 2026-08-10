---
title: "Add item to trunk"
description: "Adds items to a vehicle trunk using only the vehicle plate, automatically resolving the full inventory ID."
icon: "car-side"
---

Adds items to a vehicle trunk using only the vehicle plate, automatically resolving the full inventory ID.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:addItemToTrunk(plate, itemName, amount, metadata, slotId)
```

```lua Example
-- Add 5 water bottles to vehicle trunk
local plate = GetVehicleNumberPlateText(vehicle)
local success, result = exports['jaksam_inventory']:addItemToTrunk(plate, 'water', 5)

if not success then
    print("Failed to add item: " .. result)
end

-- Add item with metadata
local success = exports['jaksam_inventory']:addItemToTrunk("ABC 123", 'phone', 1, {
    number = "555-0123"
})
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `plate` | string | The vehicle license plate |
| `itemName` | string | The name of the item to add |
| `amount` | number | How many items to add |
| `metadata` | table | Additional data for the item |
| `slotId` | number | Specific slot to place the item in |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if items were added successfully |
| `resultCode` | string | Error message if the operation failed (e.g., "vehicle_not_found") |
| `notificationType` | string | Type of notification to show to the user |

### Notes

- Works with owned vehicles (even if not spawned/in garage)
- Works with NPC vehicles (if currently spawned)
- Automatically creates trunk inventory if it doesn't exist
- For owned vehicles, inventory is persistent (saved to database)
