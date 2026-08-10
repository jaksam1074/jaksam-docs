---
title: "Replace default notifications"
description: "Use a custom notification system instead of the default one by listening to the notify event."
icon: "bell"
---

Triggered after notifying the player client side.

```lua Event
AddEventHandler("luxury_clothes_theft:notify", function(message, uncoloredMessage)

end)
```

### Parameters

| Name               | Data Type | Description                                                |
| ------------------ | --------- | ------------------------------------------------------------ |
| `message`          | string    | Message of the notification                                  |
| `uncoloredMessage` | string    | Message of the notification but without `~r~`, `~g~`, etc.   |

## Example

```lua
RegisterNetEvent("luxury_clothes_theft:framework:ready", function()
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["luxury_clothes_theft"]:disableScriptEvent("luxury_clothes_theft:notify")
end)

RegisterNetEvent("luxury_clothes_theft:notify", function(message, uncoloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Place this code in the file `integrations/cl_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
