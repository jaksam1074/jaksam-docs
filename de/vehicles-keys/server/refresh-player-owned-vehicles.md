---
title: "Eigene Fahrzeuge des Spielers aktualisieren"
description: "Aktualisiert die Liste der eigenen Fahrzeuge eines Spielers server-seitig, z.B. nach einem Kauf."
icon: "rotate"
---

Die Nutzung dieses Exports (server-seitig) aktualisiert die Liste der Fahrzeuge des Spielers (aus `owned_vehicles` bei ESX oder `player_vehicles` bei QBCore).

```lua Export
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId, instantly)
```

### Parameter

| Name        | Datentyp | Beschreibung                                                                                                                    |
| ----------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `playerId`  | integer   | Die Server-ID des Spielers                                                                                                                  |
| `instantly` | boolean   | Optional. Standardmäßig wird 2 Sekunden gewartet, bevor aktualisiert wird. Falls du es sicher sofort benötigst, übergib `true`, ansonsten kann er weggelassen werden. |

### Beispiel

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    -- Dies aktualisiert die eigenen Fahrzeuge des Spielers, nachdem er ein Fahrzeug gekauft hat (nur ein Beispiel)

    exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId)
end)
```
