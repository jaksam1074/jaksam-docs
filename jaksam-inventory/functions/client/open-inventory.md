---
title: "Open inventory"
description: "Opens an inventory alongside the player's inventory."
icon: "door-open"
---

Opens an inventory alongside the player's inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:openInventory(inventoryId)
```

```lua Example
-- Open a stash inventory
exports['jaksam_inventory']:openInventory('police_stash_1')

-- Open a trunk inventory
exports['jaksam_inventory']:openInventory('car_trunk_123')
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string | The ID of the inventory to open |

### Return value

None. Opens the inventory UI if successful.
