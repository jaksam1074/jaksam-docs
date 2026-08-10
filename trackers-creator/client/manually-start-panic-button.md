---
title: "Manually start panic button"
description: "Trigger the panic button from your own code, without requiring the hotkey."
icon: "hand-pointer"
---

You can use this event to manually start the panic button, without requiring the player to press the hotkey at all — for example, from a radial menu.

<Note>
  The hotkey for the panic button can be disabled in the menu settings.
</Note>

```lua Event
TriggerServerEvent("trackers_creator:panicButtonPressed")
```
