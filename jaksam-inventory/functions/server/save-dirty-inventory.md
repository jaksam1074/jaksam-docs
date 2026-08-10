---
title: "Save dirty inventory"
description: "Saves a specific inventory to the database if it has been modified."
icon: "floppy-disk"
---

Saves a specific inventory to the database if it has been modified.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:saveDirtyInventory(inventoryId)
```

```lua Example
-- Save specific inventory
exports['jaksam_inventory']:saveDirtyInventory('police_stash_1')

-- Save player inventory after important changes
local success = exports['jaksam_inventory']:saveDirtyInventory(1)
if not success then
    print('Failed to save inventory')
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The ID of the inventory to save |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if inventory was saved successfully |
