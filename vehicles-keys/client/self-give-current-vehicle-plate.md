---
title: "Self give current vehicle plate"
description: "Give yourself the keys of the vehicle you're currently driving, without needing its plate."
icon: "car-side"
---

This event does the same thing as [Self give vehicle plate](/vehicles-keys/client/self-give-vehicle-plate), but it's even easier since it doesn't require any parameter — it's just a copy-paste line.

Triggering this event will automatically find the vehicle the local player is driving and give its keys to them.

```lua Event
TriggerServerEvent("vehicles_keys:selfGiveCurrentVehicleKeys")
```

## Example

```lua
-- Just an event of an imaginary driving school script
RegisterNetEvent("driving_school:test_started", function()
    local vehicle = CreateVehicle("blista", 249.40, -1407.23, 30.40, true, false)
    SetVehicleColours(vehicle, 4, 5)
    SetVehicleExtraColours(vehicle, 1, 2)
    SetEntityHeading(vehicle, 317.64)
    SetVehicleOnGroundProperly(vehicle)
    SetPedIntoVehicle(PlayerPedId(), vehicle, -1)

    -- VEHICLES KEYS INTEGRATION TO GIVE THE KEYS EASILY
    TriggerServerEvent("vehicles_keys:selfGiveCurrentVehicleKeys")
end)
```
