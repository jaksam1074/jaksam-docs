---
title: "Spieler-Shop-Objekt gekauft"
description: "Wird ausgelöst, wenn ein Spieler ein Objekt aus einem spielereigenen Shop kauft."
icon: "hand-holding-dollar"
---

Wird ausgelöst, nachdem ein Spieler ein Objekt aus einem spielereigenen Shop gekauft hat.

```lua Event
RegisterNetEvent("shops_creator:playersShops:boughtObject", function(playerId, shopId, objectId, quantity, totalPrice)

end)
```

### Parameter

| Name         | Datentyp | Beschreibung                                     |
| ------------ | --------- | -------------------------------------------------- |
| `playerId`   | integer   | Die ID des Spielers, der das Objekt gekauft hat                 |
| `shopId`     | integer   | Die Shop-ID (dieselbe, die in der Datenbank steht)   |
| `objectId`   | integer   | Die ID des gekauften Objekts                         |
| `quantity`   | integer   | Die Menge der gekauften Items                          |
| `totalPrice` | integer   | Der Gesamtpreis der gekauften Items                   |

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
