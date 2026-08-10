---
title: "Get items by name"
description: "Gets all items from an inventory by name, with optional metadata filtering."
icon: "tags"
---

Gets all items from an inventory by name, with optional metadata filtering.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemsByName(inventoryId, itemName, metadata, strict)
```

```lua Example
-- Get all bread items in player's inventory
local playerId = 1
local breads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')

print('Found ' .. #breads .. ' bread stacks')
for i = 1, #breads do
    local bread = breads[i]
    print('Slot ' .. bread.slot .. ': ' .. bread.amount .. ' breads')
end

-- Get all weapons with specific metadata (ammo = 0)
local weapons = exports['jaksam_inventory']:getItemsByName(playerId, 'WEAPON_PISTOL', {
    ammo = 0
})

-- Calculate total amount across all slots (getTotalItemAmount is suggested to use instead)
local totalBread = 0
local allBreads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')
for i = 1, #allBreads do
    totalBread = totalBread + allBreads[i].amount
end
print('Total bread amount:', totalBread)

-- Remove all bread from inventory
local breads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')
for i = 1, #breads do
    exports['jaksam_inventory']:removeItem(playerId, 'bread', breads[i].amount, nil, breads[i].slot)
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to search in. Can be a player server ID (number) or inventory ID (string) |
| `itemName` | string | The name of the items to search for |
| `metadata` | table | Metadata to match against when searching. If provided, only items with matching metadata will be returned |
| `strict` | boolean | Whether to match the metadata strictly (default: nil). If true, all metadata fields must match exactly |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `items` | table | Array of all items found matching the criteria (each with `name`, `amount`, `metadata`, `slot`). Empty table `{}` if no items found |

### Notes

- Each item includes the `slot` field indicating where it was found
- Use this when you need to process multiple stacks of the same item
- For single item lookups, prefer `getItemByName` for better performance
