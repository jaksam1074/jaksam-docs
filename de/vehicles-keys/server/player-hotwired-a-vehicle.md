---
title: "Spieler hat Fahrzeug kurzgeschlossen"
description: "Wird server-seitig ausgelöst, wenn ein Fahrzeug kurzgeschlossen wird."
icon: "bolt"
---

Wird ausgelöst, wenn ein Fahrzeug kurzgeschlossen wurde.

```lua Event
RegisterNetEvent("vehicles_keys:playerHotwiredVehicle", function(playerId, vehicleNetId)

end)
```

### Parameter

| Name           | Datentyp | Beschreibung         |
| -------------- | --------- | ---------------------- |
| `playerId`     | integer   | Server-ID des Spielers          |
| `vehicleNetId` | integer   | Fahrzeug-Netzwerk-ID          |

## Beispiel

```lua
RegisterNetEvent("vehicles_keys:playerHotwiredVehicle", function(playerId, vehicleNetId)
    local vehicle = NetworkGetEntityFromNetworkId(vehicleNetId)

    print("The player " .. GetPlayerName(playerId) .. " has just hotwired a vehicle with model " .. GetEntityModel(vehicle))
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
