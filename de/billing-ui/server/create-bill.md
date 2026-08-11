---
title: "Rechnung erstellen"
description: "Erstellt server-seitig eine neue Rechnung für einen Spieler oder eine Society."
icon: "file-circle-plus"
---

```lua Export
exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
```

### Parameter

| Name                | Datentyp | Beschreibung                                                                                                                                                              |
| -------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `senderIdentifier`   | string    | Der Identifier des Spielers, der die Rechnung erstellt. **In QBCore ist das die Citizen-ID.**                                                                                        |
| `targetIdentifier`   | string    | Der Identifier des Spielers, der die Rechnung erhält. **In QBCore ist das die Citizen-ID.**                                                                                       |
| `reason`             | string    | Der Grund der Rechnung                                                                                                                                                        |
| `amount`             | integer   | Der Betrag der Rechnung                                                                                                                                                          |
| `target`             | string    | Wer die Zahlung der Rechnung erhält. Wenn `targetType` `player` ist, ist das Ziel ein Identifier (oder die Citizen-ID in QBCore). Wenn `targetType` `society` ist, ist das Ziel z.B. `society_police`. |
| `targetType`         | string    | `player` oder `society`                                                                                                                                                                |

## Beispiel

```lua
-- ESX-Beispiel
RegisterCommand("sendInvoiceToOfflinePlayer", function(playerId, args)
    local senderIdentifier = ESX.GetPlayerFromId(playerId).identifier
    local targetIdentifier = args[1] -- Beispiel 6833b871ee066492978077ef154480366a2374b
    local reason = args[2] -- Beispiel "Speed limit exceeded"
    local amount = tonumber(args[3]) -- Beispiel 5000
    local target = "society_police"
    local targetType = "society"

    exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
end)

-- QBCore-Beispiel
RegisterCommand("sendInvoiceToOfflinePlayer", function(playerId, args)
    local senderIdentifier = QBCore.Functions.GetPlayer(playerId).PlayerData.citizenid
    local targetIdentifier = args[1] -- Beispiel GPI46753
    local reason = args[2] -- Beispiel "Speed limit exceeded"
    local amount = tonumber(args[3]) -- Beispiel 5000
    local target = "society_police"
    local targetType = "society"

    exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
end)
```
