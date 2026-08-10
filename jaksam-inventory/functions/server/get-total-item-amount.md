---
title: "Get total item amount"
description: "Returns the total amount of a specific item in an inventory, including items in containers."
icon: "hashtag"
---

Returns the total amount of a specific item in an inventory, including items in containers.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getTotalItemAmount(inventoryId, itemName, metadata, skipContainers)
```

```lua Example
-- Get total amount of bread in inventory
local total = exports['jaksam_inventory']:getTotalItemAmount(1, 'bread')

-- Get amount with specific metadata
local total = exports['jaksam_inventory']:getTotalItemAmount(1, 'weapon_pistol', {
    serial = "ABC123"
})

-- Get amount excluding containers
local total, totalNoContainers = exports['jaksam_inventory']:getTotalItemAmount(1, 'bread', nil, true)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to check |
| `itemName` | string | The name of the item to count |
| `metadata` | table | Metadata to match against when counting (if provided, only items with the same metadata AND name will be counted) |
| `skipContainers` | boolean | If true, items in containers will not be counted |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `totalAmount` | number | Total amount of the item in the inventory, including containers (only if skipContainers is false) |
| `totalAmountContainersExcluded` | number \| nil | Total amount excluding containers (only if skipContainers is false) |
