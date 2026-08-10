---
title: "Bypass start vehicle check"
description: "Bypass the vehicle start conditions using a state bag."
icon: "key"
---

You can bypass the start vehicle check by setting the state bag `canAlwaysStart` to `true`.

## Example

```lua
-- This command will make the player bypass the current vehicle start conditions
RegisterCommand("startbypass", function()
    local plyPed = PlayerPedId()
    local plyVeh = GetVehiclePedIsIn(plyPed)

    Entity(plyVeh).state.canAlwaysStart = true
end)
```

<Note>
  The bypass applies when you enter the vehicle **after** it's been enabled.
</Note>
