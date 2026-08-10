---
title: "Get item by name"
description: "Returns the first item found in the player's self inventory by name (order not guaranteed)."
icon: "tag"
---

Returns the first item found in the player's self inventory by name (order not guaranteed).

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemByName(itemName)
```

```lua Example
local item, slotId = exports['jaksam_inventory']:getItemByName('weapon_advancedrifle')

print(json.encode(item, {indent = true}), "SLOT ID: " .. slotId)
--[[
{
    "name": "weapon_advancedrifle",
    "metadata": {
        "serial": "TSK-24895-LFN"
    },
    "amount": 1
}
SLOT ID: 1
]]
```

</CodeGroup>

### Parameters

None.

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `item` | table | The item found in the player's self inventory |
| `slotId` | number | The slot ID of the item in the player's self inventory |
