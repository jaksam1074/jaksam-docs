---
title: "Spieler-ID-Schlüssel abrufen"
description: "Ruft server-seitig alle Fahrzeugschlüssel ab, die einem online Spieler gehören."
icon: "list"
---

```lua Export
exports["vehicles_keys"]:getPlayerIdKeys(playerId)
```

### Parameter

| Name       | Datentyp | Beschreibung                    |
| ---------- | --------- | ---------------------------------- |
| `playerId` | integer   | Die Server-ID des Ziel-Spielers           |

## Beispiel

```lua
Citizen.CreateThread(function()
    local playerServerId = 16

    local keys = exports["vehicles_keys"]:getPlayerIdKeys(playerServerId)

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
