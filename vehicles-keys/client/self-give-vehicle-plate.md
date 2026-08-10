---
title: "Self give vehicle plate"
description: "Give yourself the keys of a specific vehicle plate."
icon: "key"
---

You can use this event to self-give a vehicle plate, for example in the events where your framework spawns a vehicle with the `/car` command.

```lua Event
TriggerServerEvent("vehicles_keys:selfGiveVehicleKeys", plate)
```

### Note

If you want an easier way to give yourself the keys of the vehicle you're currently driving, check [this page](/vehicles-keys/client/self-give-current-vehicle-plate).
