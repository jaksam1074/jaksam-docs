---
title: "Item geerntet"
description: "Wird server-seitig ausgelöst, nachdem ein erntbares Item gesammelt wurde."
icon: "hand-holding"
---

Wird ausgelöst, nachdem ein erntbares Item geerntet wurde.

```lua Event
RegisterNetEvent("drugs_creator:harvest:itemHarvested", function(playerId, itemName, itemQuantity)

end)
```

### Parameter

| Name             | Datentyp | Beschreibung             |
| ----------------- | --------- | --------------------------- |
| `playerId`         | integer   | Server-ID des Spielers                 |
| `itemName`         | string    | ID des soeben geernteten Items             |
| `itemQuantity`     | integer   | Geerntete Item-Menge             |

## Beispiel

```lua
-- Ein Beispiel für ein XP-System
RegisterNetEvent("drugs_creator:harvest:itemHarvested", function(playerId, itemName, itemQuantity)
    TriggerEvent("xp_system:addXp", playerId, itemQuantity)
end)
```
