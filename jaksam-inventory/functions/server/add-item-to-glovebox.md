---
title: "Add item to glovebox"
description: "Adds items to a vehicle glovebox using only the vehicle plate, automatically resolving the full inventory ID."
icon: "car"
---

Adds items to a vehicle glovebox using only the vehicle plate, automatically resolving the full inventory ID.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:addItemToGlovebox(plate, itemName, amount, metadata, slotId)
```

```lua Example
-- Add documents to glovebox
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:addItemToGlovebox(plate, 'documents', 1)

-- Add multiple items
local success = exports['jaksam_inventory']:addItemToGlovebox("XYZ 789", 'money', 500)
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
- Automatically creates glovebox inventory if it doesn't exist
- For owned vehicles, inventory is persistent (saved to database)
