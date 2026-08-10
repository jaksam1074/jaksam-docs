---
title: "Vehicle locked/unlocked"
description: "Triggered server side when a vehicle's lock state changes."
icon: "lock"
---

Triggered when the vehicle lock has been toggled.

```lua Event
RegisterNetEvent("vehicles_keys:vehicleLockChanged", function(vehicle, isLocked)

end)
```

### Parameters

| Name       | Data Type | Description                            |
| ---------- | --------- | ------------------------------------------ |
| `vehicle`  | integer   | Vehicle handle                                |
| `isLocked` | boolean   | Whether the vehicle is now locked or not        |

## Example

```lua
RegisterNetEvent("vehicles_keys:vehicleLockChanged", function(vehicle, isLocked)
    print("The vehicle " .. vehicle .. " is now " .. (isLocked and "locked" or "unlocked"))
end)
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
