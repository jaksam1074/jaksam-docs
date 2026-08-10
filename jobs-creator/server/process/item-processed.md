---
title: "Item processed"
description: "Triggered when a player processes an item at a process marker."
icon: "gears"
---

Triggered when a player processes an item at a process marker.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:process:processedItem", function(playerId, markerId, addedItemName, addedItemQuantity, removedItemName, removedItemQuantity)
end)
```

```lua Example
RegisterNetEvent("jobs_creator:process:processedItem", function(playerId, markerId, addedItemName, addedItemQuantity, removedItemName, removedItemQuantity)
    TriggerEvent("xp_system:addExperience", playerId, "process")
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player's server ID |
| `markerId` | integer | Marker ID |
| `addedItemName` | string | Received item name |
| `addedItemQuantity` | integer | Received item quantity |
| `removedItemName` | string | Removed item name |
| `removedItemQuantity` | integer | Removed item quantity |