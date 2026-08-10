---
title: "Get item from slot"
description: "Gets an item from a specific slot in the player's inventory."
icon: "grid-2"
---

Gets an item from a specific slot in the player's inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemFromSlot(slotId)
```

```lua Example
-- Get item from player's slot 5
local item = exports['jaksam_inventory']:getItemFromSlot(5)

if item then
    print('Item name:', item.name)
    print('Amount:', item.amount)
    if item.metadata then
        print('Metadata:', json.encode(item.metadata))
    end
else
    print('Slot 5 is empty')
end

-- Check if a specific slot has a weapon
local slotItem = exports['jaksam_inventory']:getItemFromSlot(1)
if slotItem then
  local staticItem = exports['jaksam_inventory']:getStaticItem(slotItem.name)
  if staticItem and staticItem.type == 'weapon' then
    print('Found weapon in slot 1:', slotItem.name)
  end
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `slotId` | number | The slot number to get the item from (in the player's inventory) |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `item` | table \| nil | The item in the slot (`name`, `amount`, `metadata`), or nil if the slot is empty |
