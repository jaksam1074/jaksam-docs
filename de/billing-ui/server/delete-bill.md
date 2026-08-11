---
title: "Rechnung löschen"
description: "Löscht server-seitig eine Rechnung anhand ihrer ID."
icon: "trash"
---

```lua Export
exports["billing_ui"]:deleteBillId(billId)
```

### Parameter

| Name     | Datentyp | Beschreibung                                                    |
| -------- | --------- | ------------------------------------------------------------------ |
| `billId` | integer   | Die Rechnungs-ID, zu finden in der Datenbank-Tabelle `billing`                    |

## Beispiel

```lua
-- Beispiel-Befehl /deleteBillId 51
RegisterCommand("deleteBillId", function(playerId, args)
    local billId = tonumber(args[1])
    exports["billing_ui"]:deleteBillId(billId)
end)
```
