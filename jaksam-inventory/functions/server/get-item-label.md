---
title: "Get item label"
description: "Gets the display label of an item."
icon: "tag"
---

Gets the display label of an item.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemLabel(itemName)
```

```lua Example
-- Get item label
local label = exports['jaksam_inventory']:getItemLabel('bread')
print(label) -- prints "Bread" or whatever label is set

-- Check if item exists using label (despite this would work, the best way would be to use getStaticItem)
if not exports['jaksam_inventory']:getItemLabel('invalid_item') then
    print('Item does not exist')
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `itemName` | string | The name of the item to get the label for |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `label` | string \| nil | The display label of the item, nil if item doesn't exist |
