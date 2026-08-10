---
title: "Replace default police alert"
description: "Replace the client-side police alert behavior with your own."
icon: "siren-on"
---

<Warning>
  Triggered when police is alerted. This is triggered on **each** police player's client — if you're looking for a single event, check the server-side category.
</Warning>

```lua Event
RegisterNetEvent("vehicles_keys:alertedPolice", function(coords, message)

end)
```

### Parameters

| Name      | Data Type | Description                                |
| --------- | --------- | -------------------------------------------- |
| `coords`  | vector3   | Coordinates where the alert was triggered     |
| `message` | string    | The message the cop will see                  |

## Example

```lua
-- Disables the default police alert
RegisterNetEvent("vehicles_keys:framework:ready", function()
    exports["vehicles_keys"]:disableScriptEvent("vehicles_keys:alertedPolice")
end)

RegisterNetEvent("vehicles_keys:alertedPolice", function(coords, message)
    -- Do something
end)
```

<Note>
  Place this code in the file `integrations/cl_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
