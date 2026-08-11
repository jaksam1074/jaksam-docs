---
title: "Get inventory"
description: "Ruft vollständige Daten über ein Inventar ab, inklusive Items, Gewichtslimits und Metadaten."
icon: "boxes-stacked"
---

Ruft vollständige Daten über ein Inventar ab, inklusive Items, Gewichtslimits und Metadaten.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getInventory(inventoryId)
```

```lua Example
-- Das Inventar eines Spielers abrufen
local inventory = exports['jaksam_inventory']:getInventory(1) -- Spieler mit Server-ID 1

-- Ein Stash-Inventar abrufen
local stashInv = exports['jaksam_inventory']:getInventory('police_stash_1')

if inventory then
    print(inventory.totalWeight) -- gibt das aktuelle Gewicht aus
    print(inventory.limits.maxWeight) -- gibt das maximal erlaubte Gewicht aus
    print(json.encode(inventory.items, {indent = true})) -- {["SLOT-4"] = {name = "itemName", amount = 1, metadata = {}}}
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die Inventar-ID, deren Daten abgerufen werden sollen. Kann eine Spieler-Server-ID (number) oder Inventar-ID (string) sein |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventory` | table \| nil | `{id, label, type, options, items, totalWeight, limits: {maxSlots, maxWeight}, metadata}` |
