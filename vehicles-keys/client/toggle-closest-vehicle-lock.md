---
title: "Toggle closest vehicle lock"
description: "Manually toggle the lock of the closest vehicle."
icon: "lock"
---

This export can be used to manually toggle a vehicle's lock.

```lua Export
exports["vehicles_keys"]:toggleClosestVehicleLock()
```

## Example

```lua
RegisterCommand("togglelock", function(_, args)
    exports["vehicles_keys"]:toggleClosestVehicleLock()
end)
```
