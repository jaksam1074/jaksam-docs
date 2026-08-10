---
title: "Get owned plates of local player"
description: "Get all vehicle plates owned by the local player."
icon: "list"
---

This export gets all the owned plates of **the local player**.

```lua Export
local ownedPlates = exports["vehicles_keys"]:getOwnedVehiclePlates()
```

### Return

A table containing all the owned plates, with the following format:

```lua
{
    ["ABC123"] = {
        type = "owned",
        model = -35726841
    },

    ["BCD473"] = {
        type = "temporary",
        model = -55726841
    },
}
```
