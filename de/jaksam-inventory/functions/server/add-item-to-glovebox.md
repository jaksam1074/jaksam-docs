---
title: "Add item to glovebox"
description: "Fügt Items zu einem Fahrzeug-Handschuhfach hinzu, nur anhand des Kennzeichens, mit automatischer Auflösung der vollständigen Inventar-ID."
icon: "car"
---

Fügt Items zu einem Fahrzeug-Handschuhfach hinzu, nur anhand des Kennzeichens, mit automatischer Auflösung der vollständigen Inventar-ID.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:addItemToGlovebox(plate, itemName, amount, metadata, slotId)
```

```lua Example
-- Dokumente zum Handschuhfach hinzufügen
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:addItemToGlovebox(plate, 'documents', 1)

-- Mehrere Items hinzufügen
local success = exports['jaksam_inventory']:addItemToGlovebox("XYZ 789", 'money', 500)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `plate` | string | Das Fahrzeugkennzeichen |
| `itemName` | string | Der Name des hinzuzufügenden Items |
| `amount` | number | Wie viele Items hinzugefügt werden sollen |
| `metadata` | table | Zusätzliche Daten für das Item |
| `slotId` | number | Bestimmter Slot, in dem das Item platziert werden soll |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls die Items erfolgreich hinzugefügt wurden |
| `resultCode` | string | Fehlermeldung, falls der Vorgang fehlgeschlagen ist (z.B. "vehicle_not_found") |
| `notificationType` | string | Art der Benachrichtigung, die dem Nutzer angezeigt werden soll |

### Hinweise

- Funktioniert mit eigenen Fahrzeugen (auch wenn nicht gespawnt/in der Garage)
- Funktioniert mit NPC-Fahrzeugen (falls aktuell gespawnt)
- Erstellt bei Bedarf automatisch das Handschuhfach-Inventar
- Bei eigenen Fahrzeugen ist das Inventar persistent (in der Datenbank gespeichert)
