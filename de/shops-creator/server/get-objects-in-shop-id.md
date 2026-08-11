---
title: "Objekte in Shop-ID abrufen"
description: "Ruft ab, welche Objekte in einem bestimmten Shop verkauft oder gekauft werden."
icon: "boxes-stacked"
---

Dieser Export gibt zurück, welche Objekte in einer Shop-ID verkauft/gekauft werden.

```lua Export
local objectsInShop = getAllObjectFromPlayersShopId(shopId)
```

### Parameter

| Name     | Datentyp | Beschreibung                                     |
| -------- | --------- | -------------------------------------------------- |
| `shopId` | integer   | Die Shop-ID (dieselbe, die in der Datenbank steht)   |

### Beispiel-Ausgabe

```lua
{
	[64] = {
		["name"] = "beer",
		["price"] = 5,
		["type"] = "item",
		["quantity"] = 1,
		["label"] = "Beer",
		["method"] = "buy", -- Spieler kann das Item kaufen
		["id"] = 64,
	},
	[65] = {
		["name"] = "weed_seed",
		["price"] = 555,
		["type"] = "item",
		["quantity"] = 5,
		["label"] = "Weed Seed",
		["method"] = "sell",  -- Spieler kann das Item verkaufen
		["id"] = 65,
	},
	[63] = {
		["name"] = "accesscard",
		["price"] = 5,
		["type"] = "item",
		["quantity"] = 1,
		["label"] = "Access Card",
		["method"] = "buy", -- Spieler kann das Item kaufen
		["id"] = 63,
	},
}
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
