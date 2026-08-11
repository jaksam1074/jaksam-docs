---
title: "Schlüssel an Spieler-ID geben"
description: "Gibt server-seitig einem online Spieler Fahrzeugschlüssel."
icon: "key"
---

```lua Export
exports["vehicles_keys"]:giveVehicleKeysToPlayerId(playerId, plate, type)
```

### Parameter

| Name       | Datentyp         | Beschreibung                                                                                                  |
| ---------- | ------------------ | ------------------------------------------------------------------------------------------------------------- |
| `playerId` | integer             | Die Server-ID des Ziel-Spielers                                                                                     |
| `plate`    | string              | Das Fahrzeug-Kennzeichen                                                                                               |
| `type`     | string (optional)  | Der Fahrzeugtyp. Standardmäßig `"temporary"`. Verfügbare Typen: `"temporary"`, `"owned"`, `"other_player"`          |

## Beispiel

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    exports["vehicles_keys"]:giveVehicleKeysToPlayerId(playerId, plate, "owned")
end)
```
