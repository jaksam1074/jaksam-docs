---
title: "Item geerntet"
description: "Wird server-seitig ausgelöst, nachdem ein Item in einem Feld geerntet wurde."
icon: "hand-holding"
---

Wird ausgelöst, nachdem ein Item in einem Feld geerntet wurde.

```lua Event
RegisterNetEvent("drugs_creator:fields:itemHarvested", function(playerId, fieldId, itemName, itemQuantity)

end)
```

### Parameter

| Name             | Datentyp | Beschreibung                             |
| ----------------- | --------- | -------------------------------------------- |
| `playerId`         | integer   | Server-ID des Spielers                                 |
| `fieldId`          | integer   | Feld-ID, in dem das Item geerntet wurde              |
| `itemName`         | string    | ID des soeben geernteten Items                              |
| `itemQuantity`     | integer   | Geerntete Item-Menge                              |

## Beispiel

```lua
-- Ein Beispiel für ein XP-System
RegisterNetEvent("drugs_creator:fields:itemHarvested", function(playerId, fieldId, itemName, itemQuantity)
    TriggerEvent("xp_system:addXp", playerId, itemName, itemQuantity)
end)
```
