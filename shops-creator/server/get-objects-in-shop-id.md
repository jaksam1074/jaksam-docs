---
title: "Get objects in shop ID"
description: "Get which objects are being sold or bought in a given shop."
icon: "boxes-stacked"
---

This export returns which objects are being sold/bought in a shop ID.

```lua Export
local objectsInShop = getAllObjectFromPlayersShopId(shopId)
```

### Parameters

| Name     | Data Type | Description                                     |
| -------- | --------- | -------------------------------------------------- |
| `shopId` | integer   | The shop ID (the same one that's in the database)   |

### Output example

```lua
{
	[64] = {
		["name"] = "beer",
		["price"] = 5,
		["type"] = "item",
		["quantity"] = 1,
		["label"] = "Beer",
		["method"] = "buy", -- Player can buy the item
		["id"] = 64,
	},
	[65] = {
		["name"] = "weed_seed",
		["price"] = 555,
		["type"] = "item",
		["quantity"] = 5,
		["label"] = "Weed Seed",
		["method"] = "sell",  -- Player can sell the item
		["id"] = 65,
	},
	[63] = {
		["name"] = "accesscard",
		["price"] = 5,
		["type"] = "item",
		["quantity"] = 1,
		["label"] = "Access Card",
		["method"] = "buy", -- Player can buy the item
		["id"] = 63,
	},
}
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
