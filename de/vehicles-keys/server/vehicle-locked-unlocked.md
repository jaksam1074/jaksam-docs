---
title: "Fahrzeug ver-/entriegelt"
description: "Wird server-seitig ausgelöst, wenn sich der Schließzustand eines Fahrzeugs ändert."
icon: "lock"
---

Wird ausgelöst, wenn das Fahrzeug-Schloss umgeschaltet wurde.

```lua Event
RegisterNetEvent("vehicles_keys:vehicleLockChanged", function(vehicle, isLocked)

end)
```

### Parameter

| Name       | Datentyp | Beschreibung                            |
| ---------- | --------- | ------------------------------------------ |
| `vehicle`  | integer   | Fahrzeug-Handle                                |
| `isLocked` | boolean   | Ob das Fahrzeug jetzt verriegelt ist oder nicht        |

## Beispiel

```lua
RegisterNetEvent("vehicles_keys:vehicleLockChanged", function(vehicle, isLocked)
    print("The vehicle " .. vehicle .. " is now " .. (isLocked and "locked" or "unlocked"))
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
