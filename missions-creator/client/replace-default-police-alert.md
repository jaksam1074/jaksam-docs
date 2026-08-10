---
title: "Replace default police alert"
description: "Replace the client-side police alert behavior with your own."
icon: "siren-on"
---

<Warning>
  Triggered when police is alerted. This is triggered on **each** police player's client — if you're looking for a single event, check the server-side category.
</Warning>

```lua Event
RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)

end)
```

### Parameters

| Name      | Data Type | Description                     |
| --------- | --------- | ---------------------------------- |
| `coords`  | vector3   | Coordinates to send to police       |
| `message` | string    | The message the cop will see        |

## Example

```lua
-- Disables the default police alert
RegisterNetEvent("missions_creator:framework:ready", function()
    exports["missions_creator"]:disableScriptEvent("missions_creator:alertedPolice")
end)

RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)
    -- Do something
end)
```

<Note>
  Place this code in the file `jaksam_core/config/cl_config.lua`, at the bottom of the file on new lines.
</Note>
