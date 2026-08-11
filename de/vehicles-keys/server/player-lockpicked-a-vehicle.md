---
title: "Spieler hat Fahrzeug geknackt"
description: "Wird server-seitig ausgelöst, wenn ein Fahrzeugschloss geknackt wird."
icon: "lock-open"
---

Wird ausgelöst, wenn ein Fahrzeugschloss geknackt wurde.

```lua Event
RegisterNetEvent("vehicles_keys:playerLockpickedVehicle", function(playerId, vehicleNetId)

end)
```

### Parameter

| Name           | Datentyp | Beschreibung         |
| -------------- | --------- | ---------------------- |
| `playerId`     | integer   | Server-ID des Spielers          |
| `vehicleNetId` | integer   | Fahrzeug-Netzwerk-ID          |

## Beispiel

```lua
RegisterNetEvent("vehicles_keys:playerLockpickedVehicle", function(playerId, vehicleNetId)
    local vehicle = NetworkGetEntityFromNetworkId(vehicleNetId)

    print("The player " .. GetPlayerName(playerId) .. " has just lockpicked a vehicle with model " .. GetEntityModel(vehicle))
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
