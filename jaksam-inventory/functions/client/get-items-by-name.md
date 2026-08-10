---
title: "Get items by name"
description: "Returns all items that match a specific item name from the player's inventory, including their slot numbers."
icon: "tags"
---

Returns all items that match a specific item name from the player's inventory. Unlike `getItemByName` which returns only the first match, this function returns all occurrences with their slot numbers.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemsByName(itemName)
```

```lua Example
-- Get all bread items in inventory
local breadItems = exports['jaksam_inventory']:getItemsByName('bread')

print('Found ' .. #breadItems .. ' bread items')
for i, item in pairs(breadItems) do
    print('Slot ' .. item.slot .. ': ' .. item.amount .. 'x ' .. item.name)
end

-- Check if player has multiple weapons of the same type
local pistols = exports['jaksam_inventory']:getItemsByName('weapon_pistol')
if #pistols > 1 then
    print('Player has multiple pistols in different slots')
    for i, pistol in pairs(pistols) do
        if pistol.metadata and pistol.metadata.serial then
            print('Serial: ' .. pistol.metadata.serial .. ' in slot ' .. pistol.slot)
        end
    end
end

-- No items found scenario
local rareItems = exports['jaksam_inventory']:getItemsByName('rare_diamond')
if #rareItems == 0 then
    print('Player has no rare diamonds')
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `itemName` | string | The name of the items to search for in the player's inventory |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `items` | table | Array of all items matching the name. Each item includes `name`, `amount`, `metadata`, and `slot`. Returns empty table if no items found |
