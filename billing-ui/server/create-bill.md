---
title: "Create bill"
description: "Create a new bill for a player or society server side."
icon: "file-circle-plus"
---

```lua Export
exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
```

### Parameters

| Name                | Data Type | Description                                                                                                                                                              |
| -------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `senderIdentifier`   | string    | The identifier of the player who creates the invoice. **In QBCore it's the citizen ID.**                                                                                        |
| `targetIdentifier`   | string    | The identifier of the player who receives the invoice. **In QBCore it's the citizen ID.**                                                                                       |
| `reason`             | string    | The reason for the invoice                                                                                                                                                        |
| `amount`             | integer   | The amount of the invoice                                                                                                                                                          |
| `target`             | string    | Who will receive the payment of the invoice. If `targetType` is `player`, the target is an identifier (or citizen ID in QBCore). If `targetType` is `society`, the target is, for example, `society_police`. |
| `targetType`         | string    | `player` or `society`                                                                                                                                                                |

## Example

```lua
-- ESX example
RegisterCommand("sendInvoiceToOfflinePlayer", function(playerId, args)
    local senderIdentifier = ESX.GetPlayerFromId(playerId).identifier
    local targetIdentifier = args[1] -- Example 6833b871ee066492978077ef154480366a2374b
    local reason = args[2] -- Example "Speed limit exceeded"
    local amount = tonumber(args[3]) -- Example 5000
    local target = "society_police"
    local targetType = "society"

    exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
end)

-- QBCore example
RegisterCommand("sendInvoiceToOfflinePlayer", function(playerId, args)
    local senderIdentifier = QBCore.Functions.GetPlayer(playerId).PlayerData.citizenid
    local targetIdentifier = args[1] -- Example GPI46753
    local reason = args[2] -- Example "Speed limit exceeded"
    local amount = tonumber(args[3]) -- Example 5000
    local target = "society_police"
    local targetType = "society"

    exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
end)
```
