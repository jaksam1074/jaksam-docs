---
title: "Fahrzeugstart-Prüfung umgehen"
description: "Umgehe die Fahrzeugstart-Bedingungen mithilfe eines State Bags."
icon: "key"
---

Du kannst die Fahrzeugstart-Prüfung umgehen, indem du den State Bag `canAlwaysStart` auf `true` setzt.

## Beispiel

```lua
-- Dieser Befehl lässt den Spieler die aktuellen Fahrzeugstart-Bedingungen umgehen
RegisterCommand("startbypass", function()
    local plyPed = PlayerPedId()
    local plyVeh = GetVehiclePedIsIn(plyPed)

    Entity(plyVeh).state.canAlwaysStart = true
end)
```

<Note>
  Die Umgehung greift, wenn du das Fahrzeug betrittst, **nachdem** sie aktiviert wurde.
</Note>
