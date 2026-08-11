---
title: "Get static item"
description: "Ruft allgemeine Item-Informationen aus dem Inventar ab, wie Gewicht, Stapelbarkeit, Beschreibung, Label usw."
icon: "cube"
---

Ruft allgemeine Item-Informationen aus dem Inventar ab, wie Gewicht, Stapelbarkeit, Beschreibung, Label usw.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getStaticItem(itemName)
```

```lua Example
local item = exports['jaksam_inventory']:getStaticItem('bread')
print(item.label) -- Bread
print(item.weight) -- 1.0
print(item.stackable) -- true
print(item.description) -- A bread
print(item.maxStack) -- 100
print(item.rarity) -- common
print(item.type) -- item|container|ammo|currency
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `itemName` | string | Der Name des abzurufenden Items |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `item` | table | Die Item-Informationen. Wird das Item nicht gefunden, wird nil zurückgegeben |
