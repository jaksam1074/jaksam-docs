---
title: "Item hergestellt"
description: "Wird ausgelöst, wenn ein Spieler an einem Crafting-Table-Marker ein Item herstellt."
icon: "hammer"
---

Wird ausgelöst, wenn ein Spieler an einem Crafting-Table-Marker ein Item herstellt.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:crafting_table:craftedItem", function(playerId, markerId, itemName, itemQuantity)
end)
```

```lua Beispiel
RegisterNetEvent("jobs_creator:crafting_table:craftedItem", function(playerId, markerId, itemName, itemQuantity)
    TriggerEvent("xp_system:addExperience", playerId, "craft")
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |
| `markerId` | integer | Marker-ID |
| `itemName` | string | Name des hergestellten Items |
| `itemQuantity` | integer | Menge des hergestellten Items |
