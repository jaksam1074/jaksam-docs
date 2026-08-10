---
title: "Toggle current duty status"
description: "Trigger to toggle or explicitly set the player's current duty status."
icon: "briefcase"
---

Trigger to toggle the current duty status of the player.

## Toggle

This will toggle the current duty status of the player (if they were off duty, they will go on duty, and vice versa).

<CodeGroup>

```lua Event
TriggerEvent("jobs_creator:toggleCurrentDutyStatus")
```

```lua Example
-- Toggles the current duty status
RegisterCommand("duty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus")
end, false)
```

</CodeGroup>

## Set explicitly

This will set the duty status of the player to the given status instead of toggling it.

<CodeGroup>

```lua Event
TriggerEvent("jobs_creator:toggleCurrentDutyStatus", newDutyStatus)
```

```lua Example
RegisterCommand("onduty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus", true)
end, false)
RegisterCommand("offduty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus", false)
end, false)
```

</CodeGroup>