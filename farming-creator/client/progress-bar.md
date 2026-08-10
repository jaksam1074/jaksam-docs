---
title: "Progress bar"
description: "Replace the default progress bar with your own, or trigger the default one from external scripts."
icon: "spinner"
---

## Replace/Disable

Triggered when using the progress bar.

```lua Event
RegisterNetEvent("farming_creator:internalProgressBar", function(time, text)

end)
```

### Parameters

| Name   | Data Type | Description                       |
| ------ | --------- | ---------------------------------- |
| `time` | integer   | Progress bar duration in seconds   |
| `text` | string    | Description text                   |

### Example

```lua
-- In farming_creator/integrations/cl_integrations.lua
RegisterNetEvent("farming_creator:framework:ready", function()
    -- Disables the default script progress bar (otherwise there would be 2 progress bars)
    exports["farming_creator"]:disableScriptEvent("farming_creator:internalProgressBar")
end)

-- Example to replace the script progress bar with an external one
RegisterNetEvent("farming_creator:internalProgressBar", function(time, text)
    -- The event to activate your external progress bar
    TriggerEvent("external_progressbar:start", time, text)
end)
```

<Note>
  Place this code in the file `integrations/cl_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>

## Use in external scripts

If you like the default progress bar of the script and want to use it in external scripts, this is the event:

```lua
TriggerEvent("farming_creator:startProgressBar", timeInMS, text, hexColor)
```

### Parameters

| Name       | Data Type | Description                                                                                            |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |
| `timeInMS` | integer   | Duration of the progress bar in milliseconds                                                              |
| `text`     | string    | The text that will be shown with the progress bar                                                         |
| `hexColor` | string    | The color of the progress bar in hex code (example `#70f2b4`). Can be `nil` to use the script's default one |

### Example

```lua
-- This will create a command to show a red progress bar
-- /progressbar 5000 Hello
RegisterCommand("progressbar", function(playerId, args)
    TriggerEvent("farming_creator:startProgressBar", tonumber(args[1]), args[2], "#ff0000")
end)
```
