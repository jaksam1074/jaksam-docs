---
title: "Remove item from trunk"
description: "Entfernt Items aus einem Fahrzeugkofferraum, nur anhand des Kennzeichens, mit automatischer Auflösung der vollständigen Inventar-ID."
icon: "car-side"
---

Entfernt Items aus einem Fahrzeugkofferraum, nur anhand des Kennzeichens, mit automatischer Auflösung der vollständigen Inventar-ID.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:removeItemFromTrunk(plate, itemName, amount, metadata, slotId)
```

```lua Example
-- 3 Wasserflaschen aus dem Kofferraum entfernen
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:removeItemFromTrunk(plate, 'water', 3)

-- Aus bestimmtem Slot entfernen
local success = exports['jaksam_inventory']:removeItemFromTrunk("ABC 123", 'weapon', 1, nil, 5)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `plate` | string | Das Fahrzeugkennzeichen |
| `itemName` | string | Der Name des zu entfernenden Items |
| `amount` | number | Wie viele Items entfernt werden sollen |
| `metadata` | table | Metadaten, die beim Entfernen abgeglichen werden (optionale Filterung) |
| `slotId` | number | Bestimmter Slot, aus dem entfernt werden soll |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls die Items erfolgreich entfernt wurden |
| `resultCode` | string | Fehlermeldung, falls der Vorgang fehlgeschlagen ist |
| `notificationType` | string | Art der Benachrichtigung, die dem Nutzer angezeigt werden soll |

### Hinweise

Das Fahrzeug muss existieren (eigenes Fahrzeug in der Datenbank oder aktuell gespawntes NPC-Fahrzeug). Gibt false mit "vehicle_not_found" zurück, falls das Fahrzeug nicht existiert.
