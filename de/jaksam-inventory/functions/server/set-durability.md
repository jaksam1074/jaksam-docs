---
title: "Set durability"
description: "Setzt den Haltbarkeitswert eines Items in einem bestimmten Inventar-Slot."
icon: "gauge"
---

Setzt den Haltbarkeitswert eines Items in einem bestimmten Inventar-Slot.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setDurability(inventoryId, slotId, durability)
```

```lua Example
-- Waffenhaltbarkeit auf 75% setzen
local success, result = exports['jaksam_inventory']:setDurability(1, 5, 75)

-- Haltbarkeit nach Waffennutzung verringern
local item = exports['jaksam_inventory']:getItemFromSlot(playerId, slotId)
if item and item.metadata.durability then
    local newDurability = math.max(0, item.metadata.durability - 5)
    exports['jaksam_inventory']:setDurability(playerId, slotId, newDurability)
end

-- Haltbarkeit für ein Stash-Item setzen
exports['jaksam_inventory']:setDurability('police_stash_1', 3, 100)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die Inventar-ID, die das Item enthält. Kann eine Spieler-Server-ID oder Inventar-ID sein |
| `slotId` | number | Der Slot, der das zu aktualisierende Item enthält |
| `durability` | number | Der zu setzende Haltbarkeitswert (wird auf 0 bis 100 begrenzt) |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls die Haltbarkeit erfolgreich aktualisiert wurde |
| `resultCode` | string | Fehlermeldung, falls der Vorgang fehlgeschlagen ist |
