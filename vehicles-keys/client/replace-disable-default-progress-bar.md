---
title: "Replace/Disable default progress bar"
description: "Replace the default progress bar with your own, or trigger the default one from external scripts."
icon: "spinner"
---

Triggered when using the progress bar.

```lua Event
RegisterNetEvent("vehicles_keys:internalProgressBar", function(time, text)

end)
```

### Parameters

| Name   | Data Type | Description                       |
| ------ | --------- | ------------------------------------ |
| `time` | integer   | Progress bar duration in seconds       |
| `text` | string    | Description text                        |

## Example

```lua
-- In vehicles_keys/integrations/cl_integrations.lua
RegisterNetEvent("vehicles_keys:framework:ready", function()
    -- Disables the default script progress bar (otherwise there would be 2 progress bars)
    exports["vehicles_keys"]:disableScriptEvent("vehicles_keys:internalProgressBar")
end)

-- Example to replace the script progress bar with an external one
RegisterNetEvent("vehicles_keys:internalProgressBar", function(time, text)
    -- The event to activate your external progress bar
    TriggerEvent("external_progressbar:start", time, text)
end)
```

<Note>
  Place this code in the file `integrations/cl_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
