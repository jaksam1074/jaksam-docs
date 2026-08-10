---
title: "Save dirty inventories"
description: "Saves all modified inventories to the database."
icon: "floppy-disk"
---

Saves all modified inventories to the database.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:saveDirtyInventories()
```

```lua Example
-- Save all modified inventories
exports['jaksam_inventory']:saveDirtyInventories()

-- Good practice to save before server restart
AddEventHandler('onResourceStop', function(resourceName)
    if resourceName == GetCurrentResourceName() then
        exports['jaksam_inventory']:saveDirtyInventories()
    end
end)
```

</CodeGroup>

### Parameters

None.

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if all inventories were saved successfully |
