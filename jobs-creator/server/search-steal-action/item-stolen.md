---
title: "Item Stolen"
description: "Triggered after a player steals something from the actions menu, only if you use the default player search/rob, it won't work if you replaced it"
icon: "hand"
---

Triggered after a player steals something from the actions menu.

<Note>
  This only works if you use the default player search/rob action — it won't fire if you replaced it with a custom module.
</Note>

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:actions:itemStolen", function(playerId, targetId, itemName, itemQuantity)
end)
```

```lua Example
-- This example for ESX will "delete" all stolen items
RegisterNetEvent("jobs_creator:actions:itemStolen", function(playerId, targetId, itemName, itemQuantity)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    xPlayer.removeInventoryItem(itemName, itemQuantity)
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | The server ID of the player who stole the item |
| `targetId` | integer | The server ID of the victim who lost the item |
| `itemName` | string | Item name |
| `itemQuantity` | integer | Quantity stolen |