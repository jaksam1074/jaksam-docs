---
title: "Get items by name"
description: "Gibt alle Items mit diesem Namen aus dem Inventar des Spielers zurück, inklusive ihrer Slot-Nummern."
icon: "tags"
---

Gibt alle Items zurück, die auf einen bestimmten Item-Namen im Inventar des Spielers passen. Im Gegensatz zu `getItemByName`, das nur den ersten Treffer zurückgibt, gibt diese Funktion alle Vorkommen mit ihren Slot-Nummern zurück.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemsByName(itemName)
```

```lua Example
-- Alle Brot-Items im Inventar abrufen
local breadItems = exports['jaksam_inventory']:getItemsByName('bread')

print('Found ' .. #breadItems .. ' bread items')
for i, item in pairs(breadItems) do
    print('Slot ' .. item.slot .. ': ' .. item.amount .. 'x ' .. item.name)
end

-- Prüfen, ob der Spieler mehrere Waffen des gleichen Typs hat
local pistols = exports['jaksam_inventory']:getItemsByName('weapon_pistol')
if #pistols > 1 then
    print('Player has multiple pistols in different slots')
    for i, pistol in pairs(pistols) do
        if pistol.metadata and pistol.metadata.serial then
            print('Serial: ' .. pistol.metadata.serial .. ' in slot ' .. pistol.slot)
        end
    end
end

-- Szenario: keine Items gefunden
local rareItems = exports['jaksam_inventory']:getItemsByName('rare_diamond')
if #rareItems == 0 then
    print('Player has no rare diamonds')
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `itemName` | string | Der Name der im Inventar des Spielers zu suchenden Items |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `items` | table | Array aller Items mit passendem Namen. Jedes Item enthält `name`, `amount`, `metadata` und `slot`. Gibt eine leere Tabelle zurück, falls keine Items gefunden wurden |
