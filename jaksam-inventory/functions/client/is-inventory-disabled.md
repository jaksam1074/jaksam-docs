---
title: "Is inventory disabled"
description: "Returns whether inventory opening is currently disabled."
icon: "ban"
---

Returns whether inventory opening is currently disabled.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:isInventoryDisabled()
```

```lua Example
-- Check if inventory is disabled before doing something
local disabled = exports['jaksam_inventory']:isInventoryDisabled()

if disabled then
    print('Inventory is currently disabled')
end

-- Guard a custom action
if not exports['jaksam_inventory']:isInventoryDisabled() then
    exports['jaksam_inventory']:openInventory('my_stash')
end
```

</CodeGroup>

### Parameters

None.

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `disabled` | boolean | True if inventory opening is currently disabled, false otherwise |
