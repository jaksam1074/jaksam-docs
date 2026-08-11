---
title: "Can swap item"
description: "Prüft, ob der Tausch eines Items gegen ein anderes in einem Inventar möglich ist."
icon: "right-left"
---

Prüft, ob der Tausch von firstItem (Entfernen von firstItemCount) gegen testItem (Hinzufügen von testItemCount) möglich ist.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:canSwapItem(inventoryId, firstItem, firstItemCount, testItem, testItemCount)
```

```lua Example
-- Prüfen, ob der Spieler 5 Brot gegen 1 Wasser tauschen kann
local playerId = 1
local canSwap = exports['jaksam_inventory']:canSwapItem(playerId, 'bread', 5, 'water', 1)

if canSwap then
    exports['jaksam_inventory']:removeItem(playerId, 'bread', 5)
    exports['jaksam_inventory']:addItem(playerId, 'water', 1)
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die zu prüfende Inventar-ID. Kann eine Spieler-Server-ID oder Inventar-ID sein |
| `firstItem` | string | Der Name des zu prüfenden Items |
| `firstItemCount` | number | Wie viele Items entfernt werden sollen |
| `testItem` | string | Der Name des hinzuzufügenden Items |
| `testItemCount` | number | Wie viele Items hinzugefügt werden sollen |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `boolean` | boolean | True, falls das Inventar die Items tauschen kann, false falls der Tausch nicht möglich ist |
