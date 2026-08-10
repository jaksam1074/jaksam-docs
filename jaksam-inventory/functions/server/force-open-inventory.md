---
title: "Force open inventory"
description: "Forces an inventory to be opened for a specific player without permission checks."
icon: "door-open"
---

Forces an inventory to be opened for a specific player without permission checks.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:forceOpenInventory(playerId, inventoryId)
```

```lua Example
-- Open a stash for a player
local playerId = 1
exports['jaksam_inventory']:forceOpenInventory(playerId, 'police_stash_1')

-- Open another player's inventory (search/rob)
local targetPlayerId = 2
exports['jaksam_inventory']:forceOpenInventory(playerId, targetPlayerId)

-- Open inventory from a custom menu/UI
RegisterNetEvent('myresource:openCustomStorage', function(storageId)
    local playerId = source
    exports['jaksam_inventory']:forceOpenInventory(playerId, storageId)
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | number | The server ID of the player who will see the inventory |
| `inventoryId` | string \| number | The inventory ID to open. Can be a player server ID (number) or inventory ID (string) |

### Return value

None.
