---
title: "Can carry item"
description: "Checks if an inventory has space for additional items, considering both weight and slot limits."
icon: "weight-hanging"
---

Checks if an inventory has space for additional items, considering both weight and slot limits.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:canCarryItem(inventoryId, itemName, amount)
```

```lua Example
-- Check if player can carry 5 bread
local canCarry = exports['jaksam_inventory']:canCarryItem(1, 'bread', 5)

if canCarry then
    -- Safe to add items
    exports['jaksam_inventory']:addItem(1, 'bread', 5)
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to check. Can be a player server ID or inventory ID |
| `itemName` | string | The name of the item to check |
| `amount` | number | How many items to check for |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `boolean` | boolean | True if the inventory can carry the items, false if adding would exceed weight or slot limits |
