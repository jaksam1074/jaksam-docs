---
title: "Get inventory"
description: "Gets complete data about an inventory including its items, weight limits, and metadata."
icon: "boxes-stacked"
---

Gets complete data about an inventory including its items, weight limits, and metadata.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getInventory(inventoryId)
```

```lua Example
-- Get a player's inventory
local inventory = exports['jaksam_inventory']:getInventory(1) -- player with server ID 1

-- Get a stash inventory
local stashInv = exports['jaksam_inventory']:getInventory('police_stash_1')

if inventory then
    print(inventory.totalWeight) -- prints current weight
    print(inventory.limits.maxWeight) -- prints max weight allowed
    print(json.encode(inventory.items, {indent = true})) -- {["SLOT-4"] = {name = "itemName", amount = 1, metadata = {}}}
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to get data for. Can be a player server ID (number) or inventory ID (string) |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `inventory` | table \| nil | `{id, label, type, options, items, totalWeight, limits: {maxSlots, maxWeight}, metadata}` |
