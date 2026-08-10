---
title: "Get total item amount"
description: "Gets the total amount of a specific item in the player's inventory."
icon: "hashtag"
---

Gets the total amount of a specific item in the player's inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getTotalItemAmount(itemName, metadata)
```

```lua Example
-- Get total amount of bread
local breadCount = exports['jaksam_inventory']:getTotalItemAmount('bread')

-- Get amount of specific weapon by serial
local weaponCount = exports['jaksam_inventory']:getTotalItemAmount('weapon_pistol', {
    serial = "ABC123"
})
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `itemName` | string | The name of the item to count |
| `metadata` | table | Metadata to match against when counting (if provided, only items with the same metadata AND name will be counted) |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `totalAmount` | number | Total amount of the item in the player's inventory |
