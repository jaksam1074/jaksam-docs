---
title: "Replace default notifications"
description: "Use a custom notification system instead of the default one by listening to the notify event."
icon: "bell"
---

Triggered after notifying the player client side.

```lua Event
AddEventHandler("doors_creator:notify", function(message, uncoloredMessage)

end)
```

### Parameters

| Name               | Data Type | Description                                                |
| ------------------ | --------- | ------------------------------------------------------------ |
| `message`          | string    | Message of the notification                                  |
| `uncoloredMessage` | string    | Message of the notification but without `~r~`, `~g~`, etc.   |

## Example

```lua
RegisterNetEvent("doors_creator:framework:ready", function()
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["doors_creator"]:disableScriptEvent("doors_creator:notify")
end)

RegisterNetEvent("doors_creator:notify", function(message, uncoloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Place this code in the file `integrations/cl_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
