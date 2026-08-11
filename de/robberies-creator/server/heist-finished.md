---
title: "Heist abgeschlossen"
description: "Wird ausgelöst, wenn ein Heist abgeschlossen wird."
icon: "flag-checkered"
---

Wird ausgelöst, wenn ein Heist abgeschlossen wird (im selben Moment, in dem die Server-Konsole `"Heist has been completed"` loggt).

```lua Event
RegisterNetEvent("robberies_creator:heist:heistFinished", function(heistId)

end)
```

### Parameter

| Name      | Datentyp | Beschreibung        |
| --------- | --------- | --------------------- |
| `heistId` | integer   | ID des Heists        |

## Beispiel

```lua
RegisterNetEvent("robberies_creator:heist:heistFinished", function(heistId)
    -- nur ein Beispiel, macht nichts Sinnvolles, du möchtest vielleicht Daten aus der Datenbank abrufen

    print("Heist with ID " .. heistId .. " is finished")
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
