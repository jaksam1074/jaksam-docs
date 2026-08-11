---
title: "Schlüssel an Identifier geben"
description: "Gibt server-seitig Fahrzeugschlüssel an einen Spieler-Identifier."
icon: "key"
---

```lua Export
exports["vehicles_keys"]:giveVehicleKeysToIdentifier(identifier, plate, type)
```

### Parameter

| Name         | Datentyp         | Beschreibung                                                                                                  |
| ------------ | ------------------ | ------------------------------------------------------------------------------------------------------------- |
| `identifier` | string              | Der Identifier/die Lizenz des Ziel-Spielers                                                                            |
| `plate`      | string              | Das Fahrzeug-Kennzeichen                                                                                               |
| `type`       | string (optional)  | Der Fahrzeugtyp. Standardmäßig `"temporary"`. Verfügbare Typen: `"temporary"`, `"owned"`, `"other_player"`          |

## Beispiel

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    local identifier = xPlayer.identifier

    exports["vehicles_keys"]:giveVehicleKeysToIdentifier(identifier, plate, "owned")
end)
```
