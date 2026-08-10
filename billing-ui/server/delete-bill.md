---
title: "Delete bill"
description: "Delete a bill server side by its ID."
icon: "trash"
---

```lua Export
exports["billing_ui"]:deleteBillId(billId)
```

### Parameters

| Name     | Data Type | Description                                                    |
| -------- | --------- | ------------------------------------------------------------------ |
| `billId` | integer   | The bill ID, found in the database table `billing`                    |

## Example

```lua
-- Example command /deleteBillId 51
RegisterCommand("deleteBillId", function(playerId, args)
    local billId = tonumber(args[1])
    exports["billing_ui"]:deleteBillId(billId)
end)
```
