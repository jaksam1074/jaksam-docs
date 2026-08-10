---
title: "Progress bar"
description: "Replace the default progress bar with your own, or trigger the default one from external scripts."
icon: "spinner"
---

## How to replace it?

You can use a Robberies Creator [module](/robberies-creator/modules) if you want to use your own progress bar.

## Use in external scripts

If you like the default progress bar of the script and want to use it in external scripts, this is the event:

```lua
TriggerEvent("robberies_creator:startProgressBar", timeInMS, text, hexColor)
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
    TriggerEvent("robberies_creator:startProgressBar", tonumber(args[1]), args[2], "#ff0000")
end)
```
