---
title: "Duty status changed"
description: "Triggered after a player goes on or off duty, server side."
icon: "briefcase"
---

Triggered after a player goes on/off duty, server side.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:toggleDuty", function(playerId, jobName, isOnDuty)
end)
```

```lua Example
RegisterNetEvent("jobs_creator:toggleDuty", function(playerId, jobName, isOnDuty)
    if(isOnDuty) then
        TriggerEvent("external_scoreboard:increaseOnDutyCount", jobName)
    else
        TriggerEvent("external_scoreboard:decreaseOnDutyCount", jobName)
    end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Target player's server ID |
| `jobName` | string | Player's job ID |
| `isOnDuty` | boolean | Player's new duty status |