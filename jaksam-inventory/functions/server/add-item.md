---
title: "Add item"
description: "Adds items to an inventory with support for metadata and specific slot placement."
icon: "cube"
---

Adds items to an inventory with support for metadata and specific slot placement.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:addItem(inventoryId, itemName, amount, metadata, slotId)
```

```lua Example
-- Add 5 bread to a player's inventory
local success, result = exports['jaksam_inventory']:addItem(1, 'bread', 5)

-- Add a weapon with metadata
local success, result = exports['jaksam_inventory']:addItem(1, 'WEAPON_PISTOL', 1, {
    serial = "ABC123",
    ammo = 12
})

-- Add item to specific slot
local success, result = exports['jaksam_inventory']:addItem(1, 'bread', 1, nil, 5) -- slot 5
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to add items to. Can be a player server ID or inventory ID |
| `itemName` | string | The name of the item to add |
| `amount` | number | How many items to add |
| `metadata` | table | Additional data for the item (e.g. weapon serial, item durability) |
| `slotId` | number | Specific slot to place the item in |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if items were added successfully |
| `resultCode` | string | Error message if the operation failed |
