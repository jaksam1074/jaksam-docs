---
title: "Set durability"
description: "Sets the durability value of an item in a specific inventory slot."
icon: "gauge"
---

Sets the durability value of an item in a specific inventory slot.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setDurability(inventoryId, slotId, durability)
```

```lua Example
-- Set weapon durability to 75%
local success, result = exports['jaksam_inventory']:setDurability(1, 5, 75)

-- Decrease durability after weapon use
local item = exports['jaksam_inventory']:getItemFromSlot(playerId, slotId)
if item and item.metadata.durability then
    local newDurability = math.max(0, item.metadata.durability - 5)
    exports['jaksam_inventory']:setDurability(playerId, slotId, newDurability)
end

-- Set durability for stash item
exports['jaksam_inventory']:setDurability('police_stash_1', 3, 100)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID containing the item. Can be a player server ID or inventory ID |
| `slotId` | number | The slot containing the item to update |
| `durability` | number | The durability value to set (will be clamped between 0 and 100) |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if durability was updated successfully |
| `resultCode` | string | Error message if the operation failed |
