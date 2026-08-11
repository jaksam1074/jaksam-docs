---
title: "Get item by name"
description: "Gibt das erste im eigenen Inventar des Spielers gefundene Item mit diesem Namen zurück (Reihenfolge nicht garantiert)."
icon: "tag"
---

Gibt das erste im eigenen Inventar des Spielers gefundene Item mit diesem Namen zurück (Reihenfolge nicht garantiert).

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemByName(itemName)
```

```lua Example
local item, slotId = exports['jaksam_inventory']:getItemByName('weapon_advancedrifle')

print(json.encode(item, {indent = true}), "SLOT ID: " .. slotId)
--[[
{
    "name": "weapon_advancedrifle",
    "metadata": {
        "serial": "TSK-24895-LFN"
    },
    "amount": 1
}
SLOT ID: 1
]]
```

</CodeGroup>

### Parameter

Keine.

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `item` | table | Das im eigenen Inventar des Spielers gefundene Item |
| `slotId` | number | Die Slot-ID des Items im eigenen Inventar des Spielers |
