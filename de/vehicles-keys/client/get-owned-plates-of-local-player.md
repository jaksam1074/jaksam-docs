---
title: "Kennzeichen des lokalen Spielers abrufen"
description: "Ruft alle Fahrzeug-Kennzeichen ab, die dem lokalen Spieler gehören."
icon: "list"
---

Dieser Export ruft alle Kennzeichen ab, die **dem lokalen Spieler** gehören.

```lua Export
local ownedPlates = exports["vehicles_keys"]:getOwnedVehiclePlates()
```

### Rückgabe

Eine Table mit allen im Besitz befindlichen Kennzeichen, im folgenden Format:

```lua
{
    ["ABC123"] = {
        type = "owned",
        model = -35726841
    },

    ["BCD473"] = {
        type = "temporary",
        model = -55726841
    },
}
```
