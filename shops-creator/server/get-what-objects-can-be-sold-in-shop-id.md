---
title: "Get what objects can be sold in shop ID"
description: "Get which objects a player can sell in a shop, based on its whitelist/blacklist settings."
icon: "tags"
---

This export returns which objects the player can sell in the shop ID, depending on the shop's whitelist/blacklist and on whether the shop is allowed to manage weapons and/or items.

```lua Export
local sellableObjects = getSellableObjectsForShopId(playerId, shopId)
```

### Parameters

| Name       | Data Type | Description                                     |
| ---------- | --------- | -------------------------------------------------- |
| `playerId` | integer   | The player server ID                                |
| `shopId`   | integer   | The shop ID (the same one that's in the database)   |

### Output example

```lua
{
	[1] = {
	        ["name"] = "accesscard",
	        ["count"] = 14,
	        ["label"] = "Access Card",
	        ["type"] = "item",
        },
	[2] = {
		["name"] = "bag",
		["count"] = 49,
		["label"] = "Bag",
		["type"] = "item",
	},
	[3] = {
		["name"] = "WEAPON_COMPACTLAUNCHER",
		["count"] = 1,
		["label"] = "Compact launcher",
		["type"] = "weapon",
	},
	[4] = {
		["name"] = "WEAPON_MACHINEPISTOL",
		["count"] = 1,
		["label"] = "Machine pistol",
		["type"] = "weapon",
	}
}
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
