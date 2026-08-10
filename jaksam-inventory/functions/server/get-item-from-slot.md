---
title: "Get item from slot"
description: "Gets an item from a specific slot in an inventory."
icon: "grid-2"
---

Gets an item from a specific slot in an inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemFromSlot(inventoryId, slotId, returnRaw)
```

```lua Example
-- Get item from player's slot 5
local playerId = 1
local item = exports['jaksam_inventory']:getItemFromSlot(playerId, 5)

if item then
    print('Item name:', item.name)
    print('Amount:', item.amount)
    print('Metadata:', json.encode(item.metadata))

    item.metadata.durability = 50 -- update metadata
    exports['jaksam_inventory']:setItemMetadataInSlot(playerId, 5, item.metadata) -- save metadata
end

-- Get item from stash
local stashItem = exports['jaksam_inventory']:getItemFromSlot('police_stash_1', 3)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to get the item from. Can be a player server ID (number) or inventory ID (string) |
| `slotId` | number | The slot number to get the item from |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `item` | table \| nil | The item in the slot (`name`, `amount`, `metadata`), or nil if the slot is empty |

### Notes

<Info>
  [TODO: INFORMATION NEEDED] The export signature accepts a third `returnRaw` parameter that isn't documented in the source material used for this page.
</Info>
