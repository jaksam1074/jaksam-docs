---
title: "Verkäufliche Objekte in Shop-ID abrufen"
description: "Ruft ab, welche Objekte ein Spieler in einem Shop verkaufen kann, basierend auf dessen Whitelist-/Blacklist-Einstellungen."
icon: "tags"
---

Dieser Export gibt zurück, welche Objekte der Spieler in der Shop-ID verkaufen kann, abhängig von der Whitelist/Blacklist des Shops und davon, ob der Shop Waffen und/oder Items verwalten darf.

```lua Export
local sellableObjects = getSellableObjectsForShopId(playerId, shopId)
```

### Parameter

| Name       | Datentyp | Beschreibung                                     |
| ---------- | --------- | -------------------------------------------------- |
| `playerId` | integer   | Die Server-ID des Spielers                                |
| `shopId`   | integer   | Die Shop-ID (dieselbe, die in der Datenbank steht)   |

### Beispiel-Ausgabe

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
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
