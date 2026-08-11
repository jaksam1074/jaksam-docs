---
title: "Spieler hat neue private Frequenz gesetzt"
description: "Wird server-seitig ausgelöst, wenn ein Spieler eine neue private Tracker-Frequenz einstellt."
icon: "sliders"
---

Dieses Event wird ausgelöst, wenn ein Spieler das private Tracker-Item nutzt und eine neue Frequenz einstellt.

```lua Event
AddEventHandler("trackers_creator:playerSetNewPrivateFrequency", function(playerId, trackerId)

end)
```

### Parameter

| Name        | Datentyp | Beschreibung                 |
| ----------- | --------- | ------------------------------ |
| `playerId`  | integer   | Die Server-ID des Spielers     |
| `frequency` | integer   | Neu gewählte Frequenz            |
