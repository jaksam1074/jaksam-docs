---
title: "Item geerntet"
description: "Events, die ausgelöst werden, nachdem ein Spieler irgendwo geerntet hat - Farmen, Felder, Gießereien, Saatgut oder Werkbänke."
icon: "wheat-awn"
---

Diese Seite listet Events auf, die ausgelöst werden, **nachdem** ein Spieler irgendwo geerntet hat.

### Farmen

```lua
RegisterNetEvent("farming_creator:farms:completed", function(playerId, farmId, givenItems)
    -- Ein Beispiel für ein XP-System
    TriggerEvent("xp_system:addXp", playerId)
end)
```

### Felder

```lua
RegisterNetEvent("farming_creator:fields:completed", function(playerId, fieldId, givenItems)
    -- Ein Beispiel für ein XP-System
    TriggerEvent("xp_system:addXp", playerId)
end)
```

### Gießereien

```lua
RegisterNetEvent("farming_creator:foundries:completed", function(playerId, foundryId, givenItems)
    -- Ein Beispiel für ein XP-System
    TriggerEvent("xp_system:addXp", playerId)
end)
```

### Saatgut

```lua
RegisterNetEvent("farming_creator:seeds:interacted", function(playerId, seedId, givenItems)
    -- Ein Beispiel für ein XP-System
    TriggerEvent("xp_system:addXp", playerId)
end)
```

### Werkbänke

```lua
RegisterNetEvent("farming_creator:workbenches:completed", function(playerId, workbenchId, givenItems)
    -- Ein Beispiel für ein XP-System
    TriggerEvent("xp_system:addXp", playerId)
end)
```
