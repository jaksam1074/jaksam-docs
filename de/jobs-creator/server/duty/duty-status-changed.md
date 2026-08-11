---
title: "Duty-Status geändert"
description: "Wird ausgelöst, nachdem sich ein Spieler server-seitig an- oder abmeldet."
icon: "briefcase"
---

Wird ausgelöst, nachdem sich ein Spieler server-seitig an-/abmeldet.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:toggleDuty", function(playerId, jobName, isOnDuty)
end)
```

```lua Beispiel
RegisterNetEvent("jobs_creator:toggleDuty", function(playerId, jobName, isOnDuty)
    if(isOnDuty) then
        TriggerEvent("external_scoreboard:increaseOnDutyCount", jobName)
    else
        TriggerEvent("external_scoreboard:decreaseOnDutyCount", jobName)
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Zielspielers |
| `jobName` | string | Job-ID des Spielers |
| `isOnDuty` | boolean | Neuer Duty-Status des Spielers |
