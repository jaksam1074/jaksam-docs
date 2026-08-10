---
title: "On player fired"
description: "Triggered when a player has been fired from a job."
icon: "user-xmark"
---

Triggered when a player has been fired from a job.

```lua Event
RegisterNetEvent("jobs_creator:boss:employeeFired", function(employeeIdentifier, jobName)
end)
```

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `employeeIdentifier` | string | Player's character identifier |
| `jobName` | string | The job ID the player has been fired from |