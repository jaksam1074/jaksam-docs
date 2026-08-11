---
title: "Spieler hat Signal verloren"
description: "Wird server-seitig ausgelöst, wenn ein Spieler das Signal eines Trackers verliert."
icon: "satellite-dish"
---

Dieses Event wird ausgelöst, wenn ein Spieler das Signal eines Trackers verliert, weil er das benötigte Item verloren hat.

```lua Event
AddEventHandler("trackers_creator:playerLostSignalWithTracker", function(playerId, trackerId)

end)
```

### Parameter

| Name        | Datentyp | Beschreibung                        |
| ----------- | --------- | ------------------------------------ |
| `playerId`  | integer   | Die Server-ID des Spielers          |
| `trackerId` | integer   | Die Tracker-ID, die das Signal verloren hat      |

## Beispiel

```lua
RegisterNetEvent("trackers_creator:playerLostSignalWithTracker", function(playerId, trackerId)
    -- Du kannst hier beliebigen Code nutzen, um Daten aus der Datenbank abzurufen oder etwas anderes zu tun
end)
```
