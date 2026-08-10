---
title: "Has item"
description: "Checks if an inventory has a specific item."
icon: "circle-check"
---

Checks if an inventory has a specific item.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:hasItem(inventoryId, itemName, quantity)
```

```lua Example
-- Check if player has 5 bread
local hasItem = exports['jaksam_inventory']:hasItem(1, 'bread', 5)

if hasItem then
    -- Safe to remove items
    exports['jaksam_inventory']:removeItem(1, 'bread', 5)
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to check |
| `itemName` | string | The name of the item to check |
| `quantity` | number | How many items to check for. Default is 1 |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `boolean` | boolean | True if the inventory has the item, false if not |
