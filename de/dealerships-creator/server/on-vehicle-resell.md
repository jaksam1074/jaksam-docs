---
title: "Fahrzeug weiterverkauft"
description: "Wird server-seitig ausgelöst, nachdem ein Spieler ein Fahrzeug an ein Autohaus weiterverkauft hat."
icon: "hand-holding-dollar"
---

Dieses Event wird ausgelöst, nachdem ein Spieler ein Fahrzeug an ein Autohaus weiterverkauft hat.

```lua Event
AddEventHandler("dealerships_creator:dealerships:onVehicleResell", function(dealershipId, plate, vehicleName, playerId, resellPrice)

end)
```

### Parameter

| Name           | Datentyp | Beschreibung                                     |
| -------------- | --------- | ---------------------------------------------------- |
| `dealershipId` | integer   | Die Autohaus-ID, bei der das Fahrzeug verkauft wurde          |
| `plate`        | string    | Das Kennzeichen des Fahrzeugs                                     |
| `vehicleName`  | string    | Der Spawn-Name des Fahrzeugs                                  |
| `playerId`     | integer   | Server-ID des Spielers, der das Fahrzeug verkauft hat                  |
| `resellPrice`  | integer   | Betrag, den der Spieler erhalten hat                       |
