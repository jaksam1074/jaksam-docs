---
title: "Shop gekauft"
description: "Wird ausgelöst, wenn ein Spieler einen spielereigenen Shop kauft."
icon: "hand-holding-dollar"
---

Wird ausgelöst, nachdem ein Spieler einen spielereigenen Shop gekauft hat.

```lua Event
RegisterNetEvent("shops_creator:playersShops:shopBought", function(shopId, ownerIdentifier)

end)
```

### Parameter

| Name         | Datentyp | Beschreibung                                     |
| ------------ | --------- | -------------------------------------------------- |
| `shopId`     | integer   | Die Shop-ID (dieselbe, die in der Datenbank steht)   |
| `identifier` | string    | Der Identifier des neuen Besitzers                     |

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
