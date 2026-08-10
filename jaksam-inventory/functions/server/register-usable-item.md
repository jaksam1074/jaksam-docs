---
title: "Register usable item"
description: "Registers a callback function that will be called when an item is used."
icon: "hand-pointer"
---

Registers a callback function that will be called when an item is used. Framework specific registering item will work anyway, as `ESX.RegisterUsableItem` and QBCore's equivalent.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerUsableItem(itemName, callback)
```

```lua Example: ESX
-- Register usable item on ESX
exports['jaksam_inventory']:registerUsableItem('bread', function(playerId, itemName, inventoryItem)
    -- Heal player when bread is used
    local plyPed = GetPlayerPed(playerId)
    local health = GetEntityHealth(plyPed)
    SetEntityHealth(plyPed, math.min(health + 20, 200))
end)

-- Register usable item on ESX showing used item metadata
exports['jaksam_inventory']:registerUsableItem('armour', function(playerId, itemName, inventoryItem)
    print("Armor has still " .. inventoryItem.metadata.value .. "% of durability")
end)
```

```lua Example: QBCore
-- Register usable item on QBCore
exports['jaksam_inventory']:registerUsableItem('armour', function(playerId, item)
    print("Armor has still " .. item.metadata.value .. "% of durability")
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `itemName` | string | The name of the item to register |
| `callback` | function | Function to call when item is used. Parameters on ESX: `playerId, itemName, inventoryItem` (`name`, `metadata`, `amount`). Parameters on QBCore: `playerId, inventoryItem` (`name`, `metadata`, `amount`, etc.) |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if registration was successful |
