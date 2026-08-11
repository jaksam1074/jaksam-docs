---
title: "Get inventory"
description: "Ruft das eigene Inventar des Spielers ab."
icon: "boxes-stacked"
---

Ruft das eigene Inventar des Spielers ab.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getInventory()
```

```lua Example
local inventory = exports['jaksam_inventory']:getInventory()

print(json.encode(inventory, {indent = true}))
--[[
{
    "id": "SIV35463",
    "limits": {
        "maxSlots": 20,
        "maxWeight": 30
    },
    "items": {
        "SLOT-3": {
            "name": "money",
            "amount": 4402
        },
        "SLOT-1": {
            "name": "weapon_advancedrifle",
            "metadata": {
                "serial": "TSK-24895-LFN"
            },
            "amount": 1
        },
    },
    "label": "Inventory",
    "totalWeight": 21.0,
}
]]
```

</CodeGroup>

### Parameter

Keine.

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventory` | table | Das eigene Inventar des Spielers |
