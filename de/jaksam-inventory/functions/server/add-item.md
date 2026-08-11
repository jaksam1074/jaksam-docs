---
title: "Add item"
description: "Fügt Items zu einem Inventar hinzu, mit Unterstützung für Metadaten und bestimmte Slot-Platzierung."
icon: "cube"
---

Fügt Items zu einem Inventar hinzu, mit Unterstützung für Metadaten und bestimmte Slot-Platzierung.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:addItem(inventoryId, itemName, amount, metadata, slotId)
```

```lua Example
-- 5 Brot zum Inventar eines Spielers hinzufügen
local success, result = exports['jaksam_inventory']:addItem(1, 'bread', 5)

-- Eine Waffe mit Metadaten hinzufügen
local success, result = exports['jaksam_inventory']:addItem(1, 'WEAPON_PISTOL', 1, {
    serial = "ABC123",
    ammo = 12
})

-- Item in bestimmten Slot hinzufügen
local success, result = exports['jaksam_inventory']:addItem(1, 'bread', 1, nil, 5) -- Slot 5
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die Inventar-ID, zu der Items hinzugefügt werden sollen. Kann eine Spieler-Server-ID oder Inventar-ID sein |
| `itemName` | string | Der Name des hinzuzufügenden Items |
| `amount` | number | Wie viele Items hinzugefügt werden sollen |
| `metadata` | table | Zusätzliche Daten für das Item (z.B. Waffen-Seriennummer, Item-Haltbarkeit) |
| `slotId` | number | Bestimmter Slot, in dem das Item platziert werden soll |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls die Items erfolgreich hinzugefügt wurden |
| `resultCode` | string | Fehlermeldung, falls der Vorgang fehlgeschlagen ist |
