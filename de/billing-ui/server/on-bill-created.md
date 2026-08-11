---
title: "Rechnung erstellt"
description: "Wird server-seitig ausgelöst, nachdem eine Rechnung erstellt wurde."
icon: "file-invoice"
---

Dieses Event wird ausgelöst, nachdem eine Rechnung erstellt wurde.

```lua Event
RegisterNetEvent("billing_ui:onBillCreated", function(billId, senderIdentfier, targetIdentifier, amount, date, unixDate)

end)
```

### Parameter

| Name               | Datentyp | Beschreibung                                    |
| ------------------- | --------- | ---------------------------------------------------- |
| `billId`             | integer   | Die Rechnungs-ID                                             |
| `senderIdentfier`    | string    | Identifier des Rechnungsstellers                                   |
| `targetIdentifier`   | string    | Identifier des Rechnungsempfängers                                  |
| `amount`             | integer   | Betrag der bezahlten Rechnung                                    |
| `date`               | integer   | Erstellungsdatum der Rechnung, in lesbarer Form                 |
| `unixDate`           | integer   | Datum als Unix-Zeit                                            |
