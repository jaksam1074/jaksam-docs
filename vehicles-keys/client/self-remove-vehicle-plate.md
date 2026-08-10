---
title: "Self remove vehicle plate"
description: "Remove your own keys for a specific vehicle plate."
icon: "key"
---

You can use this event to self-remove a vehicle plate, for example in the events where your framework deletes a vehicle with the `/dv` command.

```lua Event
TriggerServerEvent("vehicles_keys:selfRemoveKeys", plate)
```
