---
title: "Rechnung aktualisieren"
description: "Aktualisiert server-seitig die Daten einer Rechnung, nachdem sie direkt in der Datenbank bearbeitet wurde."
icon: "rotate"
---

Dieser Export aktualisiert die angegebene Rechnungs-ID, sodass du, wenn du die Werte in der Datenbank bearbeitest, diesen Export nutzen kannst, um die Änderungen ohne einen Script-Neustart zu sehen.

<Note>
  Wenn du eine Rechnung löschen musst, nutze stattdessen den Export [Rechnung löschen](/de/billing-ui/server/delete-bill).
</Note>

```lua Export
exports["billing_ui"]:refreshBillId(billId)
```

### Parameter

| Name     | Datentyp | Beschreibung                                                    |
| -------- | --------- | ------------------------------------------------------------------ |
| `billId` | integer   | Die Rechnungs-ID, zu finden in der Datenbank-Tabelle `billing`                    |

## Beispiel

```lua
-- Beispiel-Befehl /refreshBillId 51
RegisterCommand("refreshBillId", function(playerId, args)
    local billId = tonumber(args[1])
    exports["billing_ui"]:refreshBillId(billId)
end)
```
