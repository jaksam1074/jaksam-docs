---
title: "Is inventory open"
description: "Checks if an inventory is currently open."
icon: "door-open"
---

Checks if an inventory is currently open. If no inventory ID is provided, returns whether the inventory UI is currently active (any inventory open). If an inventory ID is provided, checks if that specific inventory is open.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:isInventoryOpen(inventoryId)
```

```lua Example
-- Check if any inventory UI is open
local isAnyInventoryOpen = exports['jaksam_inventory']:isInventoryOpen()

if isAnyInventoryOpen then
    print('An inventory is currently open')
else
    print('No inventory is open')
end

-- Check if a specific inventory is open
local isPoliceStashOpen = exports['jaksam_inventory']:isInventoryOpen('police_stash_1')

if isPoliceStashOpen then
    print('Police stash is currently open')
end

-- Prevent opening another UI if inventory is already open
if not exports['jaksam_inventory']:isInventoryOpen() then
    -- Open custom UI
    TriggerEvent('myScript:openCustomUI')
else
    notify("Can't do it while inventory is open")
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| nil | The ID of the inventory to check. If nil, returns whether any inventory UI is currently active |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `isOpen` | boolean | True if the inventory (or any inventory UI when inventoryId is nil) is open, false otherwise |
