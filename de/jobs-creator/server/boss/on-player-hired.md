---
title: "Spieler eingestellt"
description: "Wird ausgelöst, wenn ein Spieler für einen Job eingestellt wurde."
icon: "user-plus"
---

Wird ausgelöst, wenn ein Spieler für einen Job eingestellt wurde.

```lua Event
RegisterNetEvent("jobs_creator:boss:playerHired", function(playerId, jobName)
end)
```

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |
| `jobName` | string | Die Job-ID, für die der Spieler eingestellt wurde |
