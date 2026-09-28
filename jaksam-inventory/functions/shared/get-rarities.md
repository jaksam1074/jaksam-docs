---
title: "Get rarities"
description: "Returns every rarity configured in the inventory settings, with its label and color."
icon: "gem"
---

Returns every rarity configured in the inventory settings, with its label and color. Useful to show the same rarity names and colors in your own shops, crafting menus or HUDs.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getRarities()
```

```lua Example
local rarities = exports['jaksam_inventory']:getRarities()

for rarityId, rarity in pairs(rarities) do
    print(rarityId, rarity.label, rarity.color) -- legendary  Legendary  #f0b105
end

-- Color of a specific item's rarity
local item = exports['jaksam_inventory']:getStaticItem('bread')
local color = item.rarity and rarities[item.rarity] and rarities[item.rarity].color
```

</CodeGroup>

### Parameters

None

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `rarities` | table | Rarities keyed by their ID. Each one is `{ label = string, color = string }`, where `color` is a hex color |

### Notes

- Rarities are the ones set in the `/inventory` settings menu, and the export always returns the current ones, so you can call it whenever you need them instead of caching the result on start
- The rarity ID is the value items use in their `rarity` field (see [Get static item](/jaksam-inventory/functions/shared/get-static-item))
