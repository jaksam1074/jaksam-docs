---
title: "Can carry item"
description: "Prüft, ob ein Inventar Platz für zusätzliche Items hat, unter Berücksichtigung von Gewichts- und Slot-Limits."
icon: "weight-hanging"
---

Prüft, ob ein Inventar Platz für zusätzliche Items hat, unter Berücksichtigung von Gewichts- und Slot-Limits.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:canCarryItem(inventoryId, itemName, amount)
```

```lua Example
-- Prüfen, ob der Spieler 5 Brot tragen kann
local canCarry = exports['jaksam_inventory']:canCarryItem(1, 'bread', 5)

if canCarry then
    -- Sicher, Items hinzuzufügen
    exports['jaksam_inventory']:addItem(1, 'bread', 5)
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die zu prüfende Inventar-ID. Kann eine Spieler-Server-ID oder Inventar-ID sein |
| `itemName` | string | Der Name des zu prüfenden Items |
| `amount` | number | Wie viele Items geprüft werden sollen |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `boolean` | boolean | True, falls das Inventar die Items tragen kann, false falls das Hinzufügen die Gewichts- oder Slot-Limits überschreiten würde |
