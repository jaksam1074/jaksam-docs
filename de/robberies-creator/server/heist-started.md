---
title: "Heist gestartet"
description: "Wird ausgelöst, wenn ein Heist startet."
icon: "play"
---

Wird ausgelöst, wenn ein Schritt in der ersten Stufe eines Heists abgeschlossen wird, der noch nicht gestartet ist.

```lua Event
RegisterNetEvent("robberies_creator:heist:heistStarted", function(heistId)

end)
```

### Parameter

| Name      | Datentyp | Beschreibung        |
| --------- | --------- | --------------------- |
| `heistId` | integer   | ID des Heists        |

## Beispiel

```lua
RegisterNetEvent("robberies_creator:heist:heistStarted", function(heistId)
    -- nur ein Beispiel, macht nichts Sinnvolles, du möchtest vielleicht Daten aus der Datenbank abrufen

    print("Heist with ID " .. heistId .. " has just started")
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
