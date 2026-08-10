---
title: "Can swap item"
description: "Checks if swapping one item for another in an inventory is possible."
icon: "right-left"
---

Checks if swapping firstItem (removing firstItemCount) with testItem (adding testItemCount) is possible.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:canSwapItem(inventoryId, firstItem, firstItemCount, testItem, testItemCount)
```

```lua Example
-- Check if player can swap 5 bread for 1 water
local playerId = 1
local canSwap = exports['jaksam_inventory']:canSwapItem(playerId, 'bread', 5, 'water', 1)

if canSwap then
    exports['jaksam_inventory']:removeItem(playerId, 'bread', 5)
    exports['jaksam_inventory']:addItem(playerId, 'water', 1)
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to check. Can be a player server ID or inventory ID |
| `firstItem` | string | The name of the item to check |
| `firstItemCount` | number | How many items to remove |
| `testItem` | string | The name of the item to add |
| `testItemCount` | number | How many items to add |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `boolean` | boolean | True if the inventory can swap the items, false if swapping is not possible |
