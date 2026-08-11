---
title: "Set inventory max weight"
description: "Setzt die maximale Gewichtskapazität für ein Inventar."
icon: "weight-hanging"
---

Setzt die maximale Gewichtskapazität für ein Inventar.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setInventoryMaxWeight(inventoryId, maxWeight)
```

```lua Example
-- Maximales Gewicht des Spieler-Inventars setzen
exports['jaksam_inventory']:setInventoryMaxWeight(1, 100)

-- Maximales Gewicht eines Stashs setzen
exports['jaksam_inventory']:setInventoryMaxWeight('police_stash_1', 500)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die zu ändernde Inventar-ID |
| `maxWeight` | number | Die neue maximale Gewichtskapazität |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls das Gewicht erfolgreich gesetzt wurde |
