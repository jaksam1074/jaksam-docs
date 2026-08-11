---
title: "Inventory item added"
description: "Wird ausgelöst, wenn ein Item erfolgreich zu einem Inventar hinzugefügt wurde."
icon: "circle-plus"
---

Wird ausgelöst, wenn ein Item erfolgreich zu einem Inventar hinzugefügt wurde.

<CodeGroup>

```lua Event
AddEventHandler('jaksam_inventory:onInventoryItemAdded', function(inventoryId, itemName, amount, metadata, slotId)
end)
```

```lua Example
AddEventHandler('jaksam_inventory:onInventoryItemAdded', function(inventoryId, itemName, amount, metadata, slotId)
    local inventoryType = exports['jaksam_inventory']:getInventoryType(inventoryId)
    if inventoryType ~= 'player' then return end -- Nur Spieler-Inventare behandeln

    print(string.format("Item %s (x%d) added to inventory %s", itemName, amount, inventoryId))

    -- Für QBCore: Spieler anhand der Charakter-Identifier abrufen
    local Player = exports['qb-core']:GetPlayerByCitizenId(inventoryId)
    if Player then
        local playerId = Player.PlayerData.source
        print(string.format("Player %d added item %s", playerId, itemName))
    end

    -- Für ESX: Spieler anhand der Charakter-Identifier abrufen
    -- local xPlayer = ESX.GetPlayerFromIdentifier(inventoryId)
    -- if xPlayer then
    --     local playerId = xPlayer.source
    --     print(string.format("Player %d added item %s", playerId, itemName))
    -- end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string | Die Inventar-Kennung. Bei Spielern ist das die Charakter-Identifier |
| `itemName` | string | Der Name des hinzugefügten Items |
| `amount` | number | Die hinzugefügte Menge |
| `metadata` | table | Die Metadaten des Items |
| `slotId` | number \| nil | Der Slot, zu dem das Item hinzugefügt wurde (kann nil sein, falls beim Hinzufügen kein Slot angegeben wurde) |
