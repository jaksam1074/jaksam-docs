---
title: "Tür geknackt"
description: "Wird server-seitig ausgelöst, wenn ein Spieler eine Tür knackt."
icon: "lock-open"
---

```lua Event
RegisterNetEvent("doors_creator:doorHasBeenLockpicked", function(playerId, doorId)

end)
```

### Parameter

| Name       | Datentyp | Beschreibung                                        |
| ---------- | --------- | ------------------------------------------------------ |
| `playerId` | integer   | Die Server-ID des Spielers, der die Tür geknackt hat       |
| `doorId`   | integer   | Die Tür-ID, die geknackt wurde                       |

## Beispiel

```lua
RegisterNetEvent("doors_creator:doorHasBeenLockpicked", function(playerId, doorId)
    local playerName = GetPlayerName(playerId)

    local doorData = exports["doors_creator"]:getDoorIdData(doorId)

    local doorCoords = doorData.coords

    for k, playerId in pairs(GetPlayers()) do
        local xPlayer = ESX.GetPlayerFromId(playerId)

        if(xPlayer.job.name == "police") then
            TriggerClientEvent("alert_system:alert", playerId, doorCoords, "Door has been lockpicked")
        end
    end
end)
```
