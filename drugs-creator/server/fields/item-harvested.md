---
title: "Item harvested"
description: "Triggered server side after an item is harvested in a field."
icon: "hand-holding"
---

Triggered after an item has been harvested in a field.

```lua Event
RegisterNetEvent("drugs_creator:fields:itemHarvested", function(playerId, fieldId, itemName, itemQuantity)

end)
```

### Parameters

| Name             | Data Type | Description                             |
| ----------------- | --------- | -------------------------------------------- |
| `playerId`         | integer   | Player server ID                                 |
| `fieldId`          | integer   | Field ID where the item was harvested              |
| `itemName`         | string    | Item ID just harvested                              |
| `itemQuantity`     | integer   | Item quantity harvested                              |

## Example

```lua
-- An example for a xp system
RegisterNetEvent("drugs_creator:fields:itemHarvested", function(playerId, fieldId, itemName, itemQuantity)
    TriggerEvent("xp_system:addXp", playerId, itemName, itemQuantity)
end)
```
