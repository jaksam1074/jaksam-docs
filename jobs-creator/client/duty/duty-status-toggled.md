---
title: "Duty status toggled"
description: "Triggered client side after the player goes on or off duty."
icon: "briefcase"
---

Triggered after the player goes on/off duty, client side.

<CodeGroup>

```lua Event
AddEventHandler("jobs_creator:toggleDuty", function(isOnDuty)
end)
```

```lua Example
AddEventHandler("jobs_creator:toggleDuty", function(isOnDuty)
    if(isOnDuty) then
        ESX.ShowNotification("You are now on duty")
    else
        ESX.ShowNotification("You are now off duty")
    end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `isOnDuty` | boolean | Player's new duty status |