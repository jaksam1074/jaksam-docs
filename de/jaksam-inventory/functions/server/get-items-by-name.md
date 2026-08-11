---
title: "Get items by name"
description: "Ruft alle Items mit passendem Namen aus einem Inventar ab, mit optionaler Metadaten-Filterung."
icon: "tags"
---

Ruft alle Items mit passendem Namen aus einem Inventar ab, mit optionaler Metadaten-Filterung.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemsByName(inventoryId, itemName, metadata, strict)
```

```lua Example
-- Alle Brot-Items im Inventar des Spielers abrufen
local playerId = 1
local breads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')

print('Found ' .. #breads .. ' bread stacks')
for i = 1, #breads do
    local bread = breads[i]
    print('Slot ' .. bread.slot .. ': ' .. bread.amount .. ' breads')
end

-- Alle Waffen mit bestimmten Metadaten (ammo = 0) abrufen
local weapons = exports['jaksam_inventory']:getItemsByName(playerId, 'WEAPON_PISTOL', {
    ammo = 0
})

-- Gesamtmenge über alle Slots berechnen (getTotalItemAmount wird stattdessen empfohlen)
local totalBread = 0
local allBreads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')
for i = 1, #allBreads do
    totalBread = totalBread + allBreads[i].amount
end
print('Total bread amount:', totalBread)

-- Alles Brot aus dem Inventar entfernen
local breads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')
for i = 1, #breads do
    exports['jaksam_inventory']:removeItem(playerId, 'bread', breads[i].amount, nil, breads[i].slot)
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die zu durchsuchende Inventar-ID. Kann eine Spieler-Server-ID (number) oder Inventar-ID (string) sein |
| `itemName` | string | Der Name der zu suchenden Items |
| `metadata` | table | Metadaten, gegen die bei der Suche abgeglichen wird. Falls angegeben, werden nur Items mit passenden Metadaten zurückgegeben |
| `strict` | boolean | Ob Metadaten strikt abgeglichen werden sollen (Standard: nil). Bei true müssen alle Metadaten-Felder exakt übereinstimmen |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `items` | table | Array aller passenden Items (jeweils mit `name`, `amount`, `metadata`, `slot`). Leere Tabelle `{}`, falls keine Items gefunden wurden |

### Hinweise

- Jedes Item enthält das Feld `slot`, das angibt, wo es gefunden wurde
- Nutze das, wenn du mehrere Stapel des gleichen Items verarbeiten musst
- Für einzelne Item-Abfragen ist `getItemByName` performanter
