---
title: "Get static items list"
description: "Returns the list of all items in the inventory."
icon: "list"
---

Returns the list of all items in the inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getStaticItemsList()
```

```lua Example
local items = exports['jaksam_inventory']:getStaticItemsList()
local weaponsCount = 0
for itemName, item in pairs(items) do
    if item.type == 'weapon' then
        weaponsCount = weaponsCount + 1
    end
end
print("There are in total " .. weaponsCount .. " registered weapons in the inventory")
```

</CodeGroup>

### Parameters

None.

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `items` | table | The list of items, key is the item name, value is item information (label, maxStack, weight, stackable, description, rarity, type, etc.) |
