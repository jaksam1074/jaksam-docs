---
title: "Replace default notifications"
description: "Use a custom notification system instead of the default one by listening to the notify event."
icon: "bell"
---

Triggered after notifying the player client side.

```lua Event
AddEventHandler("dealerships_creator:notify", function(message, coloredMessage)

end)
```

### Parameters

| Name              | Data Type | Description                                              |
| ------------------ | --------- | ----------------------------------------------------------- |
| `message`          | string    | Message of the notification                                  |
| `coloredMessage`   | string    | Message of the notification but with `~r~`, `~g~`, etc.       |

## Example

```lua
RegisterNetEvent("dealerships_creator:framework:ready", function()
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["dealerships_creator"]:disableScriptEvent("dealerships_creator:notify")
end)

RegisterNetEvent("dealerships_creator:notify", function(message, coloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Place this code in the file `integrations/cl_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
