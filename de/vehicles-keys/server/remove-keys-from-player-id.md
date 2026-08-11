---
title: "Schlüssel von Spieler-ID entfernen"
description: "Entfernt server-seitig Fahrzeugschlüssel von einem online Spieler."
icon: "key"
---

```lua Export
exports["vehicles_keys"]:removeKeysFromPlayerId(playerId, plate)
```

### Parameter

| Name       | Datentyp | Beschreibung                   |
| ---------- | --------- | ---------------------------------- |
| `playerId` | integer   | Die Server-ID des Ziel-Spielers           |
| `plate`    | string    | Das Fahrzeug-Kennzeichen                      |

## Beispiel

```lua
RegisterNetEvent("garage:vehicleDeleted", function(playerId, plate)
    exports["vehicles_keys"]:removeKeysFromPlayerId(playerId, plate)
end)
```
