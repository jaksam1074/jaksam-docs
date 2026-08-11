---
title: "Fahrzeug übergeben"
description: "Wird server-seitig ausgelöst, nachdem ein Spieler auf irgendeine Weise ein Fahrzeug erhalten hat."
icon: "car"
---

Dieses Event wird ausgelöst, nachdem ein Spieler auf irgendeine Weise ein Fahrzeug erhalten hat.

```lua Event
AddEventHandler("dealerships_creator:giveVehicleToPlayerId", function(playerId, vehicleName, plate)

end)
```

### Parameter

| Name          | Datentyp | Beschreibung                                   |
| ------------- | --------- | -------------------------------------------------- |
| `playerId`    | integer   | Die Server-ID des Spielers, der das Fahrzeug erhalten hat          |
| `vehicleName` | string    | Der Spawn-Name des Fahrzeugs                                |
| `plate`       | string    | Das Kennzeichen des Fahrzeugs                                    |

## Beispiel

```lua
AddEventHandler("dealerships_creator:giveVehicleToPlayerId", function(playerId, vehicleName, plate)
    -- Mach hier, was du möchtest
end)
```
