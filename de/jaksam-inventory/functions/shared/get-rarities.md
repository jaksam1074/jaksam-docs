---
title: "Get rarities"
description: "Gibt alle in den Inventar-Einstellungen konfigurierten Seltenheiten mit Label und Farbe zurück."
icon: "gem"
---

Gibt alle in den Inventar-Einstellungen konfigurierten Seltenheiten mit Label und Farbe zurück. Nützlich, um dieselben Namen und Farben der Seltenheiten in deinen eigenen Shops, Crafting-Menüs oder HUDs anzuzeigen.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getRarities()
```

```lua Example
local rarities = exports['jaksam_inventory']:getRarities()

for rarityId, rarity in pairs(rarities) do
    print(rarityId, rarity.label, rarity.color) -- legendary  Legendary  #f0b105
end

-- Farbe der Seltenheit eines bestimmten Items
local item = exports['jaksam_inventory']:getStaticItem('bread')
local color = item.rarity and rarities[item.rarity] and rarities[item.rarity].color
```

</CodeGroup>

### Parameter

Keine

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `rarities` | table | Seltenheiten nach ihrer ID. Jede ist `{ label = string, color = string }`, wobei `color` eine Hex-Farbe ist |

### Hinweise

- Die Seltenheiten sind die im Einstellungsmenü `/inventory` festgelegten, und der Export gibt immer die aktuellen zurück. Du kannst ihn also jederzeit aufrufen, statt das Ergebnis beim Start zwischenzuspeichern
- Die ID der Seltenheit ist der Wert, den Items in ihrem Feld `rarity` verwenden (siehe [Get static item](/de/jaksam-inventory/functions/shared/get-static-item))
