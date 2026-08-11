---
title: "Rechnung bezahlen"
description: "Bezahle eine Rechnung anhand ihrer ID, zum Beispiel aus einem externen Script."
icon: "credit-card"
---

Auslösen, um eine Rechnung anhand ihrer ID ordnungsgemäß zu bezahlen — du kannst dies aus externen Scripts nutzen.

```lua Event
TriggerServerEvent("billing_ui:payInvoice", billId)
```

### Parameter

| Name     | Datentyp | Beschreibung                                                  |
| -------- | --------- | ------------------------------------------------------------- |
| `billId` | integer   | Die Rechnungs-ID (aus der Datenbank-Tabelle `billing`)                 |
