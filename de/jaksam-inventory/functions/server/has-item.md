---
title: "Has item"
description: "Prüft, ob ein Inventar ein bestimmtes Item hat."
icon: "circle-check"
---

Prüft, ob ein Inventar ein bestimmtes Item hat.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:hasItem(inventoryId, itemName, quantity)
```

```lua Example
-- Prüfen, ob der Spieler 5 Brot hat
local hasItem = exports['jaksam_inventory']:hasItem(1, 'bread', 5)

if hasItem then
    -- Sicher, Items zu entfernen
    exports['jaksam_inventory']:removeItem(1, 'bread', 5)
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die zu prüfende Inventar-ID |
| `itemName` | string | Der Name des zu prüfenden Items |
| `quantity` | number | Wie viele Items geprüft werden sollen. Standard ist 1 |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `boolean` | boolean | True, falls das Inventar das Item hat, sonst false |
