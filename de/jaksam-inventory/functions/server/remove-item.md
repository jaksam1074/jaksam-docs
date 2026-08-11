---
title: "Remove item"
description: "Entfernt Items aus einem Inventar."
icon: "trash"
---

Entfernt Items aus einem Inventar.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:removeItem(inventoryId, itemName, amount, metadata, slotId)
```

```lua Example
-- 5 Brot aus dem Spieler-Inventar entfernen
local success, result = exports['jaksam_inventory']:removeItem(1, 'bread', 5)

-- Bestimmte Waffe anhand der Metadaten entfernen
local success, result = exports['jaksam_inventory']:removeItem(1, 'weapon_pistol', 1, {
    serial = "ABC123"
})

-- Aus bestimmtem Slot entfernen
local success, result = exports['jaksam_inventory']:removeItem(1, 'bread', 1, nil, 5)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die Inventar-ID, aus der Items entfernt werden sollen. Kann eine Spieler-Server-ID oder Inventar-ID sein |
| `itemName` | string | Der Name des zu entfernenden Items |
| `amount` | number | Wie viele Items entfernt werden sollen |
| `metadata` | table | Metadaten, die beim Entfernen abgeglichen werden (falls angegeben, werden nur Items mit gleicher Metadata UND gleichem Namen entfernt) |
| `slotId` | number | Bestimmter Slot, aus dem entfernt werden soll |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls die Items erfolgreich entfernt wurden |
| `resultCode` | string | Fehlermeldung, falls der Vorgang fehlgeschlagen ist |
