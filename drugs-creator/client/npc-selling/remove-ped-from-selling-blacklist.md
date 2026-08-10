---
title: "Remove ped from selling blacklist"
description: "Allow a previously blacklisted ped to be sold drugs to again."
icon: "user-check"
---

Removes a ped from the NPC selling blacklist — the opposite of the `addPedToNPCSellingBlacklist` export.

```lua Export
exports["drugs_creator"]:removePedFromNPCSellingBlacklist(ped)
```

### Parameters

| Name  | Data Type       | Description             |
| ----- | ---------------- | -------------------------- |
| `ped` | ped (integer)     | The target ped's handle       |

## Example

```lua
RegisterNetEvent('drugs_creator:framework:ready', function()
    local closestPed = ESX.Game.GetClosestPed()

    exports["drugs_creator"]:removePedFromNPCSellingBlacklist(closestPed)
end)
```
