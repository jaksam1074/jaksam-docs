---
title: "Set inventory max weight"
description: "Sets the maximum weight capacity for an inventory."
icon: "weight-hanging"
---

Sets the maximum weight capacity for an inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setInventoryMaxWeight(inventoryId, maxWeight)
```

```lua Example
-- Set player inventory max weight
exports['jaksam_inventory']:setInventoryMaxWeight(1, 100)

-- Set stash max weight
exports['jaksam_inventory']:setInventoryMaxWeight('police_stash_1', 500)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to modify |
| `maxWeight` | number | The new maximum weight capacity |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if weight was set successfully |
