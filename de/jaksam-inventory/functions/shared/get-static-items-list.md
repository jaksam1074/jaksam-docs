---
title: "Get static items list"
description: "Gibt die Liste aller Items im Inventar zurück."
icon: "list"
---

Gibt die Liste aller Items im Inventar zurück.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getStaticItemsList()
```

```lua Example
local items = exports['jaksam_inventory']:getStaticItemsList()
local weaponsCount = 0
for itemName, item in pairs(items) do
    if item.type == 'weapon' then
        weaponsCount = weaponsCount + 1
    end
end
print("There are in total " .. weaponsCount .. " registered weapons in the inventory")
```

</CodeGroup>

### Parameter

Keine.

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `items` | table | Die Liste der Items, Key ist der Item-Name, Wert sind die Item-Informationen (label, maxStack, weight, stackable, description, rarity, type, usw.) |
