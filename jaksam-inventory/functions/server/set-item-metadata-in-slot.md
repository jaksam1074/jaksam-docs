---
title: "Set item metadata in slot"
description: "Updates the metadata of an item in a specific inventory slot."
icon: "grid-2"
---

Updates the metadata of an item in a specific inventory slot.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setItemMetadataInSlot(inventoryId, slotId, metadata)
```

```lua Example
-- Update weapon ammo
exports['jaksam_inventory']:setItemMetadataInSlot(1, 5, {
    serial = "ABC123",
    ammo = 6 -- update ammo count
})

-- Update item durability
exports['jaksam_inventory']:setItemMetadataInSlot(1, 3, {
    durability = 50
})
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID containing the item |
| `slotId` | number | The slot containing the item to update |
| `metadata` | table | The new metadata to set |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if metadata was updated successfully |
| `resultCode` | string | Error message if the operation failed |
