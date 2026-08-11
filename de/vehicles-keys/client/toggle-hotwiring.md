---
title: "Kurzschließen umschalten"
description: "Aktiviere oder deaktiviere das Kurzschließen für den Spieler vorübergehend."
icon: "bolt"
---

Dieser Export ist nützlich, wenn der Spieler **vorübergehend** kein Kurzschließen mehr nutzen können soll.

```lua Export
exports["vehicles_keys"]:toggleHotwiring(newState)
```

### Parameter

| Name       | Datentyp | Beschreibung                                            |
| ---------- | --------- | ---------------------------------------------------------- |
| `newState` | boolean   | `true` = Kurzschließen aktiviert, `false` = Kurzschließen deaktiviert       |

## Beispiel

```lua
RegisterNetEvent("vehicle_shop:enteredList", function()
    exports["vehicles_keys"]:toggleHotwiring(false)
end)

RegisterNetEvent("vehicle_shop:exitedList", function()
    exports["vehicles_keys"]:toggleHotwiring(true)
end)
```
