---
title: "Inventory item transferred"
description: "Triggered when an item is successfully transferred from one inventory to another."
icon: "right-left"
---

Triggered when an item is successfully transferred from one inventory to another (including intra-inventory moves).

<CodeGroup>

```lua Event
AddEventHandler('jaksam_inventory:onInventoryItemTransferred', function(inventoryIdFrom, inventoryIdTo, itemName, amount, metadata, slotIdFrom, slotIdTo)
end)
```

```lua Example
AddEventHandler('jaksam_inventory:onInventoryItemTransferred', function(inventoryIdFrom, inventoryIdTo, itemName, amount, metadata, slotIdFrom, slotIdTo)
    local inventoryTypeFrom = exports['jaksam_inventory']:getInventoryType(inventoryIdFrom)
    local inventoryTypeTo = exports['jaksam_inventory']:getInventoryType(inventoryIdTo)
    if inventoryTypeFrom ~= 'player' or inventoryTypeTo ~= 'player' then return end -- Only handle player inventories

    print(string.format("Item %s (x%d) transferred from %s to %s", itemName, amount, inventoryIdFrom, inventoryIdTo))

    -- For QBCore
    local PlayerFrom = exports['qb-core']:GetPlayerByCitizenId(inventoryIdFrom)
    local PlayerTo = exports['qb-core']:GetPlayerByCitizenId(inventoryIdTo)

    if PlayerFrom and PlayerTo then
        local playerIdFrom = PlayerFrom.PlayerData.source
        local playerIdTo = PlayerTo.PlayerData.source
        print(string.format("Player %d transferred item %s (x%d) to player %d", playerIdFrom, itemName, amount, playerIdTo))
    end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryIdFrom` | string | The source inventory identifier. For players, this is the character identifier |
| `inventoryIdTo` | string | The destination inventory identifier. For players, this is the character identifier |
| `itemName` | string | The name of the item transferred |
| `amount` | number | The quantity transferred |
| `metadata` | table | The item's metadata |
| `slotIdFrom` | number \| nil | The slot from which the item was transferred |
| `slotIdTo` | number \| nil | The slot to which the item was transferred |

<Warning>
  The source docs noted a real Lua bug in the original example (unbalanced `end` blocks and an undefined variable) that a prior pass corrected to the working code shown above, following the same QBCore pattern as the other events. Worth double-checking it matches your actual logic.
</Warning>
