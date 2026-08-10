---
title: "Item harvested"
description: "Triggered server side after a harvestable item is collected."
icon: "hand-holding"
---

Triggered after a harvestable item has been harvested.

```lua Event
RegisterNetEvent("drugs_creator:harvest:itemHarvested", function(playerId, itemName, itemQuantity)

end)
```

### Parameters

| Name             | Data Type | Description             |
| ----------------- | --------- | --------------------------- |
| `playerId`         | integer   | Player server ID                 |
| `itemName`         | string    | Item ID just harvested             |
| `itemQuantity`     | integer   | Item quantity harvested             |

## Example

```lua
-- An example for a xp system
RegisterNetEvent("drugs_creator:harvest:itemHarvested", function(playerId, itemName, itemQuantity)
    TriggerEvent("xp_system:addXp", playerId, itemQuantity)
end)
```
