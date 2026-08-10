---
title: "Remove item"
description: "Removes items from an inventory."
icon: "trash"
---

Removes items from an inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:removeItem(inventoryId, itemName, amount, metadata, slotId)
```

```lua Example
-- Remove 5 bread from player inventory
local success, result = exports['jaksam_inventory']:removeItem(1, 'bread', 5)

-- Remove specific weapon by metadata
local success, result = exports['jaksam_inventory']:removeItem(1, 'weapon_pistol', 1, {
    serial = "ABC123"
})

-- Remove from specific slot
local success, result = exports['jaksam_inventory']:removeItem(1, 'bread', 1, nil, 5)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to remove items from. Can be a player server ID or inventory ID |
| `itemName` | string | The name of the item to remove |
| `amount` | number | How many items to remove |
| `metadata` | table | Metadata to match when removing items (if provided, only items with the same metadata AND name will be removed) |
| `slotId` | number | Specific slot to remove items from |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if items were removed successfully |
| `resultCode` | string | Error message if the operation failed |
