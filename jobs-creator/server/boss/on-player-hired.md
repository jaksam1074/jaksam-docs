---
title: "On player hired"
description: "Triggered when a player has been hired for a job."
icon: "user-plus"
---

Triggered when a player has been hired for a job.

```lua Event
RegisterNetEvent("jobs_creator:boss:playerHired", function(playerId, jobName)
end)
```

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player's server ID |
| `jobName` | string | The job ID the player has been hired for |