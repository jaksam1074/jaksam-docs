---
title: "Prüfen, ob Spieler-ID Kennzeichen besitzt"
description: "Prüft server-seitig, ob ein bestimmter Spieler ein Fahrzeug-Kennzeichen besitzt."
icon: "circle-question"
---

Dieser Export kann genutzt werden, um zu erfahren, ob ein Spieler ein Fahrzeug-Kennzeichen besitzt (kann auch geteilte, temporäre, usw. prüfen).

```lua Export
exports["vehicles_keys"]:isPlayerOwnerOfVehiclePlate(playerId, plate, onlyOwnedVehicles)
```

### Parameter

| Name                 | Datentyp | Beschreibung                                                                                     |
| --------------------- | --------- | ---------------------------------------------------------------------------------------------------- |
| `playerId`             | integer   | Die Server-ID des Spielers                                                                                   |
| `plate`                | string    | Das zu prüfende Fahrzeug-Kennzeichen                                                                              |
| `onlyOwnedVehicles`    | boolean   | `true` = nur eigene Fahrzeuge durchsuchen. `false` = auch temporäre Fahrzeuge, geteilte Schlüssel, usw. durchsuchen         |

### Rückgabe

`true`, wenn das Fahrzeug im Besitz ist.

`false`, wenn das Fahrzeug nicht im Besitz ist.

## Beispiel

```lua
RegisterCommand("checkPlate", function(playerId, args)
    local plate = args[1] -- Beispiel "ABC 123"

    if(exports["vehicles_keys"]:isPlayerOwnerOfVehiclePlate(playerId, plate, false)) then
        print("I own this vehicle plate")
    else
        print("I DO NOT own this vehicle plate")
    end
end)
```
