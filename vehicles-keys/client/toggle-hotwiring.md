---
title: "Toggle hotwiring"
description: "Temporarily enable or disable hotwiring for the player."
icon: "bolt"
---

This export is useful when you want the player to **temporarily** not be able to use hotwiring anymore.

```lua Export
exports["vehicles_keys"]:toggleHotwiring(newState)
```

### Parameters

| Name       | Data Type | Description                                            |
| ---------- | --------- | ---------------------------------------------------------- |
| `newState` | boolean   | `true` = hotwiring enabled, `false` = hotwiring disabled       |

## Example

```lua
RegisterNetEvent("vehicle_shop:enteredList", function()
    exports["vehicles_keys"]:toggleHotwiring(false)
end)

RegisterNetEvent("vehicle_shop:exitedList", function()
    exports["vehicles_keys"]:toggleHotwiring(true)
end)
```
