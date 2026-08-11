---
title: "Im Boot verkauft"
description: "Wird server-seitig ausgelöst, nachdem ein Spieler Drogen in einem Boot verkauft hat."
icon: "sailboat"
---

Wird ausgelöst, nachdem ein Spieler in einem Boot verkauft hat (für jedes verkaufte Item).

```lua Event
RegisterNetEvent("drugs_creator:boat:soldItem", function(playerId, drugName, drugQuantity, totalDrugPrice, accountName)

end)
```

### Parameter

| Name              | Datentyp | Beschreibung                                                |
| ------------------ | --------- | -------------------------------------------------------------- |
| `playerId`          | integer   | Server-ID des Spielers                                                   |
| `drugName`          | string    | ID der soeben verkauften Droge                                        |
| `drugQuantity`      | integer   | Verkaufte Item-Menge                                                     |
| `totalDrugPrice`    | integer   | Gesamtbetrag, den der Spieler erhalten hat                                    |
| `accountName`       | string    | Für die Belohnung genutzter Kontotyp (money, black_money, usw.)               |

## Beispiel

```lua
RegisterNetEvent("drugs_creator:boat:soldItem", function(playerId, drugName, drugQuantity, totalDrugPrice, accountName)
    local xPlayer = ESX.GetPlayerFromId(playerId)

    local random = math.random(1, 2)

    if(drugName == "weed" and random == 1) then
        xPlayer.addInventoryItem("weed", 3)

        xPlayer.showNotification("Here you have 3 bonus weed")
    end

    print("Player received " .. totalDrugPrice .. " in " .. accountName)
end)
```
