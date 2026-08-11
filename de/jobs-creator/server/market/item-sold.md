---
title: "Item verkauft"
description: "Wird ausgelöst, wenn ein Spieler an einem Market-Marker ein Item oder eine Waffe verkauft."
icon: "store"
---

Wird ausgelöst, wenn ein Spieler an einem Market-Marker ein Item/eine Waffe verkauft.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:market:soldItem", function(playerId, markerId, itemName, itemQuantity, totalPrice)
end)
```

```lua Beispiel
RegisterNetEvent("jobs_creator:market:soldItem", function(playerId, markerId, itemName, itemQuantity, totalPrice)
    print("Spieler-ID: " .. playerId .. " hat x" .. itemQuantity .. " " .. itemName .. " aus Shop " .. markerId .. " verkauft")
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |
| `markerId` | integer | Marker-ID |
| `itemName` | string | Item- oder Waffenname |
| `itemQuantity` | integer | Verkaufte Menge |
| `totalPrice` | integer | Erhaltener Gesamtbetrag |
