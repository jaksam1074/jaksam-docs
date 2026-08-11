---
title: "Schlüssel von Identifier entfernen"
description: "Entfernt server-seitig Fahrzeugschlüssel von einem Spieler-Identifier."
icon: "key"
---

```lua Export
exports["vehicles_keys"]:removeKeysFromIdentifier(identifier, plate)
```

### Parameter

| Name         | Datentyp | Beschreibung                     |
| ------------ | --------- | ----------------------------------- |
| `identifier` | string    | Der Identifier des Ziel-Spielers           |
| `plate`      | string    | Das Fahrzeug-Kennzeichen                       |

## Beispiel

```lua
RegisterNetEvent("garage:vehicleDeleted", function(playerId, plate)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    local identifier = xPlayer.identifier

    exports["vehicles_keys"]:removeKeysFromIdentifier(identifier, plate)
end)
```
