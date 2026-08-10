---
title: "Add ped to selling blacklist"
description: "Prevent a specific ped from being sold drugs to, for example shop keepers or dealers."
icon: "user-slash"
---

Adds a ped to the NPC selling blacklist, so players won't be able to sell to that ped (example: blackjack dealers, shop keepers, etc.).

<Note>
  If you prefer an easier way, you can blacklist entire ped models in `drugs_creator/integrations/cl_integrations.lua`.
</Note>

```lua Export
exports["drugs_creator"]:addPedToNPCSellingBlacklist(ped)
```

### Parameters

| Name  | Data Type       | Description             |
| ----- | ---------------- | -------------------------- |
| `ped` | ped (integer)     | The target ped's handle       |

## Example

```lua
RegisterNetEvent('drugs_creator:framework:ready', function()
    local closestPed = ESX.Game.GetClosestPed()

    exports["drugs_creator"]:addPedToNPCSellingBlacklist(closestPed)
end)
```
