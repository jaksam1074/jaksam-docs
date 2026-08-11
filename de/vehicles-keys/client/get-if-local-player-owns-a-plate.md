---
title: "Prüfen, ob lokaler Spieler Kennzeichen besitzt"
description: "Prüft, ob der lokale Spieler ein bestimmtes Fahrzeug-Kennzeichen besitzt."
icon: "circle-question"
---

Dieser Export kann genutzt werden, um zu erfahren, ob **der lokale Spieler** ein Fahrzeug-Kennzeichen besitzt. Er prüft auch geteilte, temporäre, usw.

```lua Export
exports["vehicles_keys"]:doesPlayerOwnPlate(plate)
```

### Parameter

| Name    | Datentyp | Beschreibung                  |
| ------- | --------- | -------------------------------- |
| `plate` | string    | Das zu prüfende Fahrzeug-Kennzeichen          |

### Rückgabe

`true`, wenn das Fahrzeug im Besitz ist.

`false`, wenn das Fahrzeug nicht im Besitz ist.

## Beispiel

```lua
RegisterCommand("checkPlate", function(_, args)
    local plate = args[1] -- Beispiel "ABC 123"

    if(exports["vehicles_keys"]:doesPlayerOwnPlate(plate)) then
        print("I own this vehicle plate")
    else
        print("I DO NOT own this vehicle plate")
    end
end)
```
