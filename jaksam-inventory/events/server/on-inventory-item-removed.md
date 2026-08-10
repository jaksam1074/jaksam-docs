---
title: "Inventory item removed"
description: "Triggered when an item is successfully removed from an inventory."
icon: "circle-minus"
---

Triggered when an item is successfully removed from an inventory.

<CodeGroup>

```lua Event
AddEventHandler('jaksam_inventory:onInventoryItemRemoved', function(inventoryId, itemName, amount, metadata, slotId)
end)
```

```lua Example
AddEventHandler('jaksam_inventory:onInventoryItemRemoved', function(inventoryId, itemName, amount, metadata, slotId)
    local inventoryType = exports['jaksam_inventory']:getInventoryType(inventoryId)
    if inventoryType ~= 'player' then return end -- Only handle player inventories

    print(string.format("Item %s (x%d) removed from inventory %s", itemName, amount, inventoryId))

    -- For QBCore: Get player by character identifier
    local Player = exports['qb-core']:GetPlayerByCitizenId(inventoryId)
    if Player then
        local playerId = Player.PlayerData.source
        print(string.format("Player %d removed item %s", playerId, itemName))

        -- Example: Log to Discord or database
        -- exports['your_logs']:log({
        --     event = "item_removed",
        --     playerId = playerId,
        --     item = itemName,
        --     amount = amount
        -- })
    end

    -- For ESX: Get player by character identifier
    -- local xPlayer = ESX.GetPlayerFromIdentifier(inventoryId)
    -- if xPlayer then
    --     local playerId = xPlayer.source
    --     print(string.format("Player %d removed item %s", playerId, itemName))
    -- end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string | The inventory identifier. For players, this is the character identifier |
| `itemName` | string | The name of the item removed |
| `amount` | number | The quantity removed |
| `metadata` | table | The item's metadata |
| `slotId` | number \| nil | The slot from which the item was removed (can be nil if a slot wasn't specified when removing item) |
