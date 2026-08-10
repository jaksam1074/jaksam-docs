---
title: "Successful craft"
description: "Triggered server side after a successful craft in a laboratory."
icon: "flask-round-potion"
---

Triggered after a successful craft in a laboratory.

```lua Event
RegisterNetEvent("drugs_creator:laboratory:successfulCraft", function(playerId, ingredientsUsed, itemsToGive, laboratoryId)

end)
```

### Parameters

| Name                | Data Type     | Description                                                                                                    |
| -------------------- | -------------- | -------------------------------------------------------------------------------------------------------------- |
| `playerId`            | integer         | Player server ID                                                                                                    |
| `ingredientsUsed`     | table           | Table containing the ingredients used. Key = ingredient name, Value = ingredient quantity                            |
| `itemsToGive`         | table/array     | An array of tables representing the items to give. Each table has `itemName` and `itemQuantity` properties            |
| `laboratoryId`        | integer         | Laboratory ID                                                                                                        |

## Example

```lua
-- An example for a xp system
RegisterNetEvent("drugs_creator:laboratory:successfulCraft", function(playerId, ingredientsUsed, itemsToGive, laboratoryId)
    for k, resultItem in pairs(itemsToGive) do
        local itemName = resultItem.itemName
        local quantity = resultItem.itemQuantity

        TriggerEvent("xp_system:addXp", playerId, quantity)
    end
end)
```
