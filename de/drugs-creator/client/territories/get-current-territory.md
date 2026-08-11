---
title: "Aktuelles Territorium abrufen"
description: "Ruft den Namen des Territoriums ab, in dem sich der lokale Spieler aktuell befindet."
icon: "map-pin"
---

Gibt den Namen des Territoriums zurück, in dem sich der lokale Spieler aktuell befindet, oder `nil`, falls außerhalb eines Territoriums.

```lua Export
local territoryName = exports["drugs_creator"]:getCurrentTerritory()
```

### Rückgabe

| Datentyp      | Beschreibung                                     |
| --------------- | -------------------------------------------------- |
| string / nil    | Der Territoriumsname, oder `nil`, falls sich der Spieler nicht in einem befindet |

## Beispiel

```lua
local territory = exports["drugs_creator"]:getCurrentTerritory()

if territory then
    print("You are in territory: " .. territory)
else
    print("You are not inside any territory")
end
```
