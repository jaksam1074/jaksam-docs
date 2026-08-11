---
title: "Alarm aktiviert (NPC-Fahrzeug)"
description: "Wird server-seitig ausgelöst, wenn ein Alarm an einem NPC-Fahrzeug aktiviert wird."
icon: "car-side"
---

Wird ausgelöst, wenn ein Alarm an einem NPC-Fahrzeug ausgelöst wird.

```lua Event
RegisterNetEvent("vehicles_keys:alarmOnNPCVehicle", function(vehicle, vehicleCoords)

end)
```

### Parameter

| Name            | Datentyp | Beschreibung                     |
| --------------- | --------- | ------------------------------------ |
| `vehicle`       | integer   | Fahrzeug-Handle                          |
| `vehicleCoords` | vector3   | Die Koordinaten des Fahrzeugs            |

## Beispiel

```lua
RegisterNetEvent("vehicles_keys:alarmOnNPCVehicle", function(vehicle, vehicleCoords)
    -- Du kannst hier eine externe Benachrichtigung hinzufügen, falls gewünscht
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
