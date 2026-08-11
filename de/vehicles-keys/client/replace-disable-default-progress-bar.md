---
title: "Standard-Fortschrittsbalken ersetzen/deaktivieren"
description: "Ersetze den Standard-Fortschrittsbalken durch deinen eigenen, oder löse den Standard-Balken aus externen Scripts aus."
icon: "spinner"
---

Wird ausgelöst, wenn der Fortschrittsbalken genutzt wird.

```lua Event
RegisterNetEvent("vehicles_keys:internalProgressBar", function(time, text)

end)
```

### Parameter

| Name   | Datentyp | Beschreibung                       |
| ------ | --------- | ------------------------------------ |
| `time` | integer   | Dauer des Fortschrittsbalkens in Sekunden       |
| `text` | string    | Beschreibungstext                        |

## Beispiel

```lua
-- In vehicles_keys/integrations/cl_integrations.lua
RegisterNetEvent("vehicles_keys:framework:ready", function()
    -- Deaktiviert den Standard-Fortschrittsbalken des Scripts (sonst gäbe es 2 Fortschrittsbalken)
    exports["vehicles_keys"]:disableScriptEvent("vehicles_keys:internalProgressBar")
end)

-- Beispiel, um den Fortschrittsbalken des Scripts durch einen externen zu ersetzen
RegisterNetEvent("vehicles_keys:internalProgressBar", function(time, text)
    -- Das Event, um deinen externen Fortschrittsbalken zu aktivieren
    TriggerEvent("external_progressbar:start", time, text)
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/cl_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
