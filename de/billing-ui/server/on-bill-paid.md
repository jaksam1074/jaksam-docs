---
title: "Rechnung bezahlt"
description: "Wird server-seitig ausgelöst, nachdem eine Rechnung bezahlt wurde."
icon: "circle-check"
---

Dieses Event wird ausgelöst, nachdem eine Rechnung bezahlt wurde.

```lua Event
RegisterNetEvent("billing_ui:onBillPaid", function(billId, senderIdentfier, targetIdentifier, amount, date, unixDate)

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
