---
title: "Get item label"
description: "Gets only the label (display name) of an item. A simpler and faster alternative to getStaticItem when you only need the item's label."
icon: "tag"
---

Gets only the label (display name) of an item. This is a simpler and faster alternative to `getStaticItem` when you only need the item's label.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemLabel(itemName)
```

```lua Example
local label = exports['jaksam_inventory']:getItemLabel('bread')
print(label) -- Bread

-- Item not found returns nil
local notFound = exports['jaksam_inventory']:getItemLabel('invalid_item')
print(notFound) -- nil
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `itemName` | string | The name of the item to get the label for |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `label` | string \| nil | The label (display name) of the item, or nil if the item is not found |
