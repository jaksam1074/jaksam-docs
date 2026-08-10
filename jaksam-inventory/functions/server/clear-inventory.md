---
title: "Clear inventory"
description: "Removes all items from an inventory, with optional exclusion of specific items."
icon: "trash"
---

Removes all items from an inventory, with optional exclusion of specific items.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:clearInventory(inventoryId, excludedItems)
```

```lua Example
local playerId = 14

-- Clear all items from player inventory
local success = exports['jaksam_inventory']:clearInventory(playerId)

-- Clear inventory but keep specific items
local success = exports['jaksam_inventory']:clearInventory(playerId, 'phone') -- keep phone

-- Clear inventory but keep multiple items
local success = exports['jaksam_inventory']:clearInventory(1, {'phone', 'id_card', 'driver_license'})

-- Clear stash inventory
local success = exports['jaksam_inventory']:clearInventory('police_stash_1')
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to clear. Can be a player server ID or inventory ID |
| `excludedItems` | string \| table | Items to exclude from clearing (keep in inventory). Can be a single item name (string) or an array of item names (table). If not provided, all items will be removed |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if inventory was cleared successfully, false if inventory doesn't exist or database update failed |
