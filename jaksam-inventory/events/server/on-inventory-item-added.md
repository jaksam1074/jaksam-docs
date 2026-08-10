---
title: "Inventory item added"
description: "Triggered when an item is successfully added to an inventory."
icon: "circle-plus"
---

Triggered when an item is successfully added to an inventory.

<CodeGroup>

```lua Event
AddEventHandler('jaksam_inventory:onInventoryItemAdded', function(inventoryId, itemName, amount, metadata, slotId)
end)
```

```lua Example
AddEventHandler('jaksam_inventory:onInventoryItemAdded', function(inventoryId, itemName, amount, metadata, slotId)
    local inventoryType = exports['jaksam_inventory']:getInventoryType(inventoryId)
    if inventoryType ~= 'player' then return end -- Only handle player inventories

    print(string.format("Item %s (x%d) added to inventory %s", itemName, amount, inventoryId))

    -- For QBCore: Get player by character identifier
    local Player = exports['qb-core']:GetPlayerByCitizenId(inventoryId)
    if Player then
        local playerId = Player.PlayerData.source
        print(string.format("Player %d added item %s", playerId, itemName))
    end

    -- For ESX: Get player by character identifier
    -- local xPlayer = ESX.GetPlayerFromIdentifier(inventoryId)
    -- if xPlayer then
    --     local playerId = xPlayer.source
    --     print(string.format("Player %d added item %s", playerId, itemName))
    -- end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string | The inventory identifier. For players, this is the character identifier |
| `itemName` | string | The name of the item added |
| `amount` | number | The quantity added |
| `metadata` | table | The item's metadata |
| `slotId` | number \| nil | The slot where the item was added (can be nil if a slot wasn't specified when adding item) |
