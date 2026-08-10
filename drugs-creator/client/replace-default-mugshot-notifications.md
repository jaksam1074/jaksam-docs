---
title: "Replace default mugshot notifications"
description: "Replace the notification shown when a ped refuses a drug during NPC selling."
icon: "id-card"
---

Notification shown when a ped refuses the drug in NPC selling (notification with the ped's face).

```lua Event
AddEventHandler("drugs_creator:internalMugshotNotify", function(ped, title, message)

end)
```

### Parameters

| Name      | Data Type | Description                   |
| --------- | --------- | ---------------------------------- |
| `ped`     | integer   | Ped entity handle                     |
| `title`   | string    | Title of the notification               |
| `message` | string    | Message of the notification              |

## Example

```lua
RegisterNetEvent("drugs_creator:framework:ready", function()
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["drugs_creator"]:disableScriptEvent("drugs_creator:internalMugshotNotify")
end)

RegisterNetEvent("drugs_creator:internalMugshotNotify", function(ped, title, message)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Place this code in the file `integrations/cl_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
