---
title: "Get static item"
description: "Gets generic item information from the inventory, like weight, stackable, description, label, etc."
icon: "cube"
---

Gets generic item information from the inventory, like weight, stackable, description, label, etc.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getStaticItem(itemName)
```

```lua Example
local item = exports['jaksam_inventory']:getStaticItem('bread')
print(item.label) -- Bread
print(item.weight) -- 1.0
print(item.stackable) -- true
print(item.description) -- A bread
print(item.maxStack) -- 100
print(item.rarity) -- common
print(item.type) -- item|container|ammo|currency
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `itemName` | string | The name of the item to get |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `item` | table | The item information. If the item is not found, returns nil |
