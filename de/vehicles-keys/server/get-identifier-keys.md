---
title: "Identifier-Schlüssel abrufen"
description: "Ruft server-seitig alle Fahrzeugschlüssel ab, die einem Spieler-Identifier gehören."
icon: "list"
---

```lua Export
exports["vehicles_keys"]:getIdentifierKeys(identifier)
```

### Parameter

| Name         | Datentyp | Beschreibung                           |
| ------------ | --------- | ---------------------------------------- |
| `identifier` | string    | Der Identifier/die Lizenz des Ziel-Spielers       |

## Beispiel

```lua
Citizen.CreateThread(function()
    local identifier = "abcedfghj12356"

    local keys = exports["vehicles_keys"]:getIdentifierKeys(identifier)

    print(ESX.DumpTable(keys))

    --[[
        Beispiel-Ausgabe

        {
            ["ABC123"] = {
                ["type"] = "owned",
                ["model"] = -563445643
            },

            ["VEG643"] = {
                ["type"] = "temporary",
                ["model"] = 165445642
            },

            ["AEC613"] = {
                ["type"] = "other_player",
                ["model"] = 1732123
            },
        }
    ]]

end)
```
