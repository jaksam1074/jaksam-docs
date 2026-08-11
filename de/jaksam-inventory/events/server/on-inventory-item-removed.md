---
title: "Inventory item removed"
description: "Wird ausgelöst, wenn ein Item erfolgreich aus einem Inventar entfernt wurde."
icon: "circle-minus"
---

Wird ausgelöst, wenn ein Item erfolgreich aus einem Inventar entfernt wurde.

<CodeGroup>

```lua Event
AddEventHandler('jaksam_inventory:onInventoryItemRemoved', function(inventoryId, itemName, amount, metadata, slotId)
end)
```

```lua Example
AddEventHandler('jaksam_inventory:onInventoryItemRemoved', function(inventoryId, itemName, amount, metadata, slotId)
    local inventoryType = exports['jaksam_inventory']:getInventoryType(inventoryId)
    if inventoryType ~= 'player' then return end -- Nur Spieler-Inventare behandeln

    print(string.format("Item %s (x%d) removed from inventory %s", itemName, amount, inventoryId))

    -- Für QBCore: Spieler anhand der Charakter-Identifier abrufen
    local Player = exports['qb-core']:GetPlayerByCitizenId(inventoryId)
    if Player then
        local playerId = Player.PlayerData.source
        print(string.format("Player %d removed item %s", playerId, itemName))

        -- Beispiel: In Discord oder Datenbank loggen
        -- exports['your_logs']:log({
        --     event = "item_removed",
        --     playerId = playerId,
        --     item = itemName,
        --     amount = amount
        -- })
    end

    -- Für ESX: Spieler anhand der Charakter-Identifier abrufen
    -- local xPlayer = ESX.GetPlayerFromIdentifier(inventoryId)
    -- if xPlayer then
    --     local playerId = xPlayer.source
    --     print(string.format("Player %d removed item %s", playerId, itemName))
    -- end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string | Die Inventar-Kennung. Bei Spielern ist das die Charakter-Identifier |
| `itemName` | string | Der Name des entfernten Items |
| `amount` | number | Die entfernte Menge |
| `metadata` | table | Die Metadaten des Items |
| `slotId` | number \| nil | Der Slot, aus dem das Item entfernt wurde (kann nil sein, falls beim Entfernen kein Slot angegeben wurde) |
