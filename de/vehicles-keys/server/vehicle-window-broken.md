---
title: "Fahrzeugfenster zerstört"
description: "Wird server-seitig ausgelöst, wenn ein Spieler ein Fahrzeugfenster zerstört."
icon: "car-burst"
---

```lua Event
RegisterNetEvent("vehicles_keys:vehicleWindowBroken", function(playerId, vehicleNetId)

end)
```

### Parameter

| Name           | Datentyp | Beschreibung                              |
| -------------- | --------- | -------------------------------------------- |
| `playerId`     | integer   | Die Server-ID des Spielers, der das Fenster zerstört hat       |
| `vehicleNetId` | integer   | Die Fahrzeug-Netzwerk-ID                             |

## Beispiel

```lua
RegisterNetEvent("vehicles_keys:vehicleWindowBroken", function(playerId, vehicleNetId)
    local vehicle = NetworkGetEntityFromNetworkId(vehicleNetId)

    print(GetPlayerName(playerId) .. " broke the window of plate " .. GetVehicleNumberPlateText(vehicle))
end)
```
