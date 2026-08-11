---
title: "Item verarbeitet"
description: "Wird ausgelöst, wenn ein Spieler an einem Process-Marker ein Item verarbeitet."
icon: "gears"
---

Wird ausgelöst, wenn ein Spieler an einem Process-Marker ein Item verarbeitet.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:process:processedItem", function(playerId, markerId, addedItemName, addedItemQuantity, removedItemName, removedItemQuantity)
end)
```

```lua Beispiel
RegisterNetEvent("jobs_creator:process:processedItem", function(playerId, markerId, addedItemName, addedItemQuantity, removedItemName, removedItemQuantity)
    TriggerEvent("xp_system:addExperience", playerId, "process")
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |
| `markerId` | integer | Marker-ID |
| `addedItemName` | string | Name des erhaltenen Items |
| `addedItemQuantity` | integer | Menge des erhaltenen Items |
| `removedItemName` | string | Name des entfernten Items |
| `removedItemQuantity` | integer | Menge des entfernten Items |
