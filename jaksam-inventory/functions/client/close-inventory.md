---
title: "Close inventory"
description: "Closes the inventory UI. Can either close a specific inventory or close the entire inventory UI."
icon: "door-closed"
---

Closes the inventory UI. Can either close a specific inventory or close the entire inventory UI.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:closeInventory(inventoryId)
```

```lua Example
-- Close the entire inventory UI
exports['jaksam_inventory']:closeInventory()

-- Close a specific inventory (e.g., a stash)
exports['jaksam_inventory']:closeInventory('police_stash_1')

-- Force close inventory after a specific event
AddEventHandler('myScript:forceCloseInventory', function()
    exports['jaksam_inventory']:closeInventory()
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| nil | If provided, removes only the specified inventory from the UI. If nil, closes the entire inventory UI and all open inventories |

### Return value

None.
