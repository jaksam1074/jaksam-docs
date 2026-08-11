---
title: "Admin-Shop-Objekt verkauft"
description: "Wird ausgelöst, wenn ein Spieler ein Objekt an einen Admin-Shop verkauft."
icon: "hand-holding-dollar"
---

Wird ausgelöst, nachdem ein Spieler ein Objekt an einen Admin-Shop verkauft hat.

```lua Event
RegisterNetEvent("shops_creator:adminShops:soldObject", function(playerId, shopId, itemId, quantity, totalPrice)

end)
```

### Parameter

| Name         | Datentyp | Beschreibung                                     |
| ------------ | --------- | -------------------------------------------------- |
| `playerId`   | integer   | Die ID des Spielers, der das Objekt verkauft hat                    |
| `shopId`     | integer   | Die Shop-ID (dieselbe, die in der Datenbank steht)   |
| `itemId`     | string    | Die ID des verkauften Items                             |
| `quantity`   | integer   | Die Menge der verkauften Items                             |
| `totalPrice` | integer   | Der Gesamtpreis der verkauften Items                      |

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
