---
title: "Nächste Tür abrufen"
description: "Ruft die nächste aktive Tür zum Spieler ab."
icon: "door-closed"
---

Gibt die nächste **aktive** Tür zum Spieler zurück.

```lua Export
exports["doors_creator"]:getClosestActiveDoor()
```

### Rückgabe

| Name       | Datentyp | Beschreibung                                       |
| ---------- | --------- | ----------------------------------------------------- |
| `door`     | table     | Table mit `door.id` und `door.object`            |
| `distance` | float     | Entfernung zur Tür                                  |

## Beispiel

```lua
Citizen.CreateThread(function()
    local closestDoor, closestDist = exports["doors_creator"]:getClosestActiveDoor()

    if(closestDoor and closestDist < 3.0) then
        print("The closest door is " .. closestDoor.id .. " and is " .. closestDist .. " meters away")
    end
end)
```
