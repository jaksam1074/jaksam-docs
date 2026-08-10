---
title: "Replace default help notifications"
description: "Replace the default 'Press E to ...' help notification with your own."
icon: "circle-info"
---

Used to show the usual `Press E to ...` text at the top left of the player's screen.

```lua Export
exports["missions_creator"]:replaceShowHelpNotification(customFunction)
```

### Parameters

| Name             | Data Type | Description                                                                                                    |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------------------- |
| `customFunction` | function  | A function that replaces the default `ESX.ShowHelpNotification` method. **Requires** the message parameter and is called each frame |

## Example

```lua
local function myCustomHelpNotification(message)
    -- Customize your function to fit your needs
    print(message)

    ExternalScript.showHelpNotification(message)
end

RegisterNetEvent("missions_creator:framework:ready", function()
    -- This will replace the base function with the one you want
    exports["missions_creator"]:replaceShowHelpNotification(myCustomHelpNotification)
end)
```

<Note>
  Place this code in the file `jaksam_core/config/cl_config.lua`, at the bottom of the file on new lines.
</Note>
