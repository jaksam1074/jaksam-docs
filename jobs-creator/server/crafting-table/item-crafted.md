---
title: "Item crafted"
description: "Triggered when a player crafts an item at a crafting table marker."
icon: "hammer"
---

Triggered when a player crafts an item at a crafting table marker.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:crafting_table:craftedItem", function(playerId, markerId, itemName, itemQuantity)
end)
```

```lua Example
RegisterNetEvent("jobs_creator:crafting_table:craftedItem", function(playerId, markerId, itemName, itemQuantity)
    TriggerEvent("xp_system:addExperience", playerId, "craft")
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player's server ID |
| `markerId` | integer | Marker ID |
| `itemName` | string | Crafted item name |
| `itemQuantity` | integer | Crafted item quantity |