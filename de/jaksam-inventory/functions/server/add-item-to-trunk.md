---
title: "Add item to trunk"
description: "Fügt Items zu einem Fahrzeugkofferraum hinzu, nur anhand des Kennzeichens, mit automatischer Auflösung der vollständigen Inventar-ID."
icon: "car-side"
---

Fügt Items zu einem Fahrzeugkofferraum hinzu, nur anhand des Kennzeichens, mit automatischer Auflösung der vollständigen Inventar-ID.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:addItemToTrunk(plate, itemName, amount, metadata, slotId)
```

```lua Example
-- 5 Wasserflaschen zum Fahrzeugkofferraum hinzufügen
local plate = GetVehicleNumberPlateText(vehicle)
local success, result = exports['jaksam_inventory']:addItemToTrunk(plate, 'water', 5)

if not success then
    print("Failed to add item: " .. result)
end

-- Item mit Metadaten hinzufügen
local success = exports['jaksam_inventory']:addItemToTrunk("ABC 123", 'phone', 1, {
    number = "555-0123"
})
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
- Erstellt bei Bedarf automatisch das Kofferraum-Inventar
- Bei eigenen Fahrzeugen ist das Inventar persistent (in der Datenbank gespeichert)
