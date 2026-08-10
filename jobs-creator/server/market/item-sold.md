---
title: "Item sold"
description: "Triggered when a player sells an item or weapon at a market marker."
icon: "store"
---

Triggered when a player sells an item/weapon at a market marker.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:market:soldItem", function(playerId, markerId, itemName, itemQuantity, totalPrice)
end)
```

```lua Example
RegisterNetEvent("jobs_creator:market:soldItem", function(playerId, markerId, itemName, itemQuantity, totalPrice)
    print("Player ID: " .. playerId .. " sold x" .. itemQuantity .. " " .. itemName .. " from shop " .. markerId)
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player's server ID |
| `markerId` | integer | Marker ID |
| `itemName` | string | Item name or weapon name |
| `itemQuantity` | integer | Sold quantity |
| `totalPrice` | integer | Total money received |