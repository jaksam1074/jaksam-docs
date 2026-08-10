---
title: "Replace default mugshot notifications"
description: "Replace the notification shown for the 'talk to ped' action (with NPC face)."
icon: "id-card"
---

Notification shown when using the "talk to ped" action (notification with NPC face).

```lua Event
AddEventHandler("missions_creator:internalMugshotNotify", function(ped, title, message)

end)
```

### Parameters

| Name      | Data Type | Description                   |
| --------- | --------- | -------------------------------- |
| `ped`     | integer   | Ped entity handle                |
| `title`   | string    | Title of the notification         |
| `message` | string    | Message of the notification       |

## Example

```lua
RegisterNetEvent("missions_creator:framework:ready", function()
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["missions_creator"]:disableScriptEvent("missions_creator:internalMugshotNotify")
end)

RegisterNetEvent("missions_creator:internalMugshotNotify", function(ped, title, message)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Place this code in the file `jaksam_core/config/cl_config.lua`, at the bottom of the file on new lines.
</Note>
