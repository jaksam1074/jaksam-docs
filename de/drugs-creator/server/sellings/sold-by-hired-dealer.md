---
title: "Von angeheuertem Dealer verkauft"
description: "Wird server-seitig ausgelöst, wenn ein angeheuerter Dealer eine Droge verkauft."
icon: "user-tie"
---

Wird server-seitig ausgelöst, wenn ein angeheuerter Dealer eine Droge verkauft.

```lua Event
AddEventHandler("drugs_creator:hiredDealers:itemSold", function(ownerIdentifier, ownerJob, drugName, quantity, totalPrice, territoryName, accountName)

end)
```

### Parameter

| Name               | Datentyp | Beschreibung                                              |
| -------------------- | --------- | ------------------------------------------------------------ |
| `ownerIdentifier`    | string    | Character-Identifier des Dealer-Besitzers                       |
| `ownerJob`           | string    | Job-/Gang-Name des Besitzers zum Zeitpunkt der Anheuerung                   |
| `drugName`           | string    | ID der verkauften Droge                                             |
| `quantity`           | integer   | Verkaufte Menge                                                          |
| `totalPrice`         | integer   | Gesamtbetrag, der beim Verkauf verdient wurde                                        |
| `territoryName`      | string    | Name des Territoriums, in dem sich der Dealer befindet                         |
| `accountName`        | string    | Für die Belohnung genutzter Kontotyp (money, black_money, usw.)                 |

## Beispiel

```lua
AddEventHandler("drugs_creator:hiredDealers:itemSold", function(ownerIdentifier, ownerJob, drugName, quantity, totalPrice, territoryName, accountName)
    print(("[Hired Dealer] %s sold %dx %s for $%d in %s (owner: %s, account: %s)"):format(
        ownerJob, quantity, drugName, totalPrice, territoryName, ownerIdentifier, accountName
    ))
end)
```
