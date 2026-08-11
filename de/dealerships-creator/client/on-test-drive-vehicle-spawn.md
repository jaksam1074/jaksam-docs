---
title: "Testfahrt-Fahrzeug gespawnt"
description: "Wird client-seitig ausgelöst, nachdem ein Testfahrt-Fahrzeug gespawnt wurde."
icon: "car-side"
---

Dieses Event wird ausgelöst, nachdem ein Testfahrt-Fahrzeug auf dem Client des Spielers gespawnt wurde, der die Testfahrt macht.

```lua Event
AddEventHandler("dealerships_creator:testDrive:vehicleSpawned", function(vehicle, vehicleNetId, plate)

end)
```

### Parameter

| Name           | Datentyp | Beschreibung               |
| -------------- | --------- | ---------------------------- |
| `vehicle`      | integer   | Das Fahrzeug-Handle             |
| `vehicleNetId` | integer   | Die Fahrzeug-Netzwerk-ID          |
| `plate`        | string    | Das Kennzeichen des Fahrzeugs             |

## Beispiel

```lua
AddEventHandler("dealerships_creator:testDrive:vehicleSpawned", function(vehicle, vehicleNetId, plate)
    SetVehicleFuelLevel(vehicle, 100.0)

    -- Du möchtest vielleicht auf irgendeine Weise Fahrzeugschlüssel vergeben
end)
```
