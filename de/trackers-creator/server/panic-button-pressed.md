---
title: "Panik-Knopf gedrückt"
description: "Wird server-seitig ausgelöst, wenn ein Spieler den Panik-Knopf nutzt."
icon: "triangle-exclamation"
---

Dieses Event wird ausgelöst, wenn ein Spieler den Panik-Knopf nutzt.

```lua Event
AddEventHandler("trackers_creator:playerPressedPanicButton", function(playerId)

end)
```

### Parameter

| Name       | Datentyp | Beschreibung                                              |
| ---------- | --------- | ---------------------------------------------------------- |
| `playerId` | integer   | Die Server-ID des Spielers, der den Panik-Knopf gedrückt hat   |

## Beispiel

```lua
RegisterNetEvent("trackers_creator:playerPressedPanicButton", function(playerId)
    local name = GetPlayerName(playerId)
    local plyPed = GetPlayerPed(playerId)
    local coords = GetEntityCoords(plyPed)

    print("Player " .. name .. " pressed panic button in coordinates " .. tostring(coords))
end)
```
