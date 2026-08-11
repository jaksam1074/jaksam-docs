---
title: "Alarm aktiviert (Spieler-Fahrzeug)"
description: "Wird server-seitig ausgelöst, wenn ein Alarm an einem Spieler-Fahrzeug aktiviert wird."
icon: "car"
---

Wird ausgelöst, wenn ein Alarm an einem Spieler-Fahrzeug aktiviert wird.

```lua Event
RegisterNetEvent("vehicles_keys:alarmOnPlayerVehicle", function(vehicle, vehicleCoords, alarmLevel)

end)
```

### Parameter

| Name            | Datentyp | Beschreibung                       |
| --------------- | --------- | -------------------------------------- |
| `vehicle`       | integer   | Fahrzeug-Handle                            |
| `vehicleCoords` | vector3   | Die Koordinaten des Fahrzeugs              |
| `alarmLevel`    | integer   | Die Stufe des installierten Alarms             |

## Beispiel

```lua
RegisterNetEvent("vehicles_keys:alarmOnPlayerVehicle", function(vehicle, vehicleCoords, alarmLevel)
    -- Du kannst hier eine externe Benachrichtigung hinzufügen, falls gewünscht
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
