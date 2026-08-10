---
title: "Refresh bill"
description: "Refresh a bill's data server side after editing it directly in the database."
icon: "rotate"
---

This export refreshes the specified bill ID, so if you edit the values in the database, you can use this export to see the changes without requiring a script restart.

<Note>
  If you need to delete a bill, use the [delete bill](/billing-ui/server/delete-bill) export instead.
</Note>

```lua Export
exports["billing_ui"]:refreshBillId(billId)
```

### Parameters

| Name     | Data Type | Description                                                    |
| -------- | --------- | ------------------------------------------------------------------ |
| `billId` | integer   | The bill ID, found in the database table `billing`                    |

## Example

```lua
-- Example command /refreshBillId 51
RegisterCommand("refreshBillId", function(playerId, args)
    local billId = tonumber(args[1])
    exports["billing_ui"]:refreshBillId(billId)
end)
```
