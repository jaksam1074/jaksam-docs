---
title: "Sold by hired dealer"
description: "Triggered server side when a hired dealer sells a drug."
icon: "user-tie"
---

Triggered on the server when a hired dealer sells a drug.

```lua Event
AddEventHandler("drugs_creator:hiredDealers:itemSold", function(ownerIdentifier, ownerJob, drugName, quantity, totalPrice, territoryName, accountName)

end)
```

### Parameters

| Name               | Data Type | Description                                              |
| -------------------- | --------- | ------------------------------------------------------------ |
| `ownerIdentifier`    | string    | Character identifier of the dealer's owner                       |
| `ownerJob`           | string    | Job/gang name of the owner at the time of hiring                   |
| `drugName`           | string    | Item ID of the drug sold                                             |
| `quantity`           | integer   | Quantity sold                                                          |
| `totalPrice`         | integer   | Total money earned from the sale                                        |
| `territoryName`      | string    | Name of the territory where the dealer is located                         |
| `accountName`        | string    | Account type used for the reward (money, black_money, etc.)                 |

## Example

```lua
AddEventHandler("drugs_creator:hiredDealers:itemSold", function(ownerIdentifier, ownerJob, drugName, quantity, totalPrice, territoryName, accountName)
    print(("[Hired Dealer] %s sold %dx %s for $%d in %s (owner: %s, account: %s)"):format(
        ownerJob, quantity, drugName, totalPrice, territoryName, ownerIdentifier, accountName
    ))
end)
```
