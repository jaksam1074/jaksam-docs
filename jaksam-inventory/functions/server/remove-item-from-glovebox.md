---
title: "Remove item from glovebox"
description: "Removes items from a vehicle glovebox using only the vehicle plate, automatically resolving the full inventory ID."
icon: "car"
---

Removes items from a vehicle glovebox using only the vehicle plate, automatically resolving the full inventory ID.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:removeItemFromGlovebox(plate, itemName, amount, metadata, slotId)
```

```lua Example
-- Remove documents from glovebox
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:removeItemFromGlovebox(plate, 'documents', 1)

if not success then
    print("Document not found in glovebox")
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `plate` | string | The vehicle license plate |
| `itemName` | string | The name of the item to remove |
| `amount` | number | How many items to remove |
| `metadata` | table | Metadata to match for removal (optional filtering) |
| `slotId` | number | Specific slot to remove from |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if items were removed successfully |
| `resultCode` | string | Error message if the operation failed |
| `notificationType` | string | Type of notification to show to the user |

### Notes

Vehicle must exist (owned vehicle in database or NPC vehicle currently spawned). Returns false with "vehicle_not_found" if vehicle doesn't exist.
