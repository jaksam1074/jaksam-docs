---
title: "Open menu manually"
description: "Trigger the Blips Creator menu to open from your own client-side code."
icon: "map-location-dot"
---

You can use this event from anywhere **client side** to open the menu.

```lua Event
TriggerEvent("blips_creator:openBlipsMenu")
```

## Example

You can open the menu with a command, for example:

```lua
RegisterCommand("blipscreator", function()
    TriggerEvent("blips_creator:openBlipsMenu")
end)
```
