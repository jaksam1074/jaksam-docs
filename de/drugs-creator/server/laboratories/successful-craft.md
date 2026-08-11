---
title: "Erfolgreiches Craften"
description: "Wird server-seitig ausgelöst, nachdem in einem Labor erfolgreich gecraftet wurde."
icon: "flask-round-potion"
---

Wird ausgelöst, nachdem in einem Labor erfolgreich gecraftet wurde.

```lua Event
RegisterNetEvent("drugs_creator:laboratory:successfulCraft", function(playerId, ingredientsUsed, itemsToGive, laboratoryId)

end)
```

### Parameter

| Name                | Datentyp     | Beschreibung                                                                                                    |
| -------------------- | -------------- | -------------------------------------------------------------------------------------------------------------- |
| `playerId`            | integer         | Server-ID des Spielers                                                                                                    |
| `ingredientsUsed`     | table           | Table mit den genutzten Zutaten. Key = Zutatenname, Value = Zutatenmenge                            |
| `itemsToGive`         | table/array     | Ein Array von Tables, die die zu gebenden Items darstellen. Jede Table hat die Eigenschaften `itemName` und `itemQuantity`            |
| `laboratoryId`        | integer         | Labor-ID                                                                                                        |

## Beispiel

```lua
-- Ein Beispiel für ein XP-System
RegisterNetEvent("drugs_creator:laboratory:successfulCraft", function(playerId, ingredientsUsed, itemsToGive, laboratoryId)
    for k, resultItem in pairs(itemsToGive) do
        local itemName = resultItem.itemName
        local quantity = resultItem.itemQuantity

        TriggerEvent("xp_system:addXp", playerId, quantity)
    end
end)
```
