---
title: "Fortschrittsbalken"
description: "Ersetze den Standard-Fortschrittsbalken durch deinen eigenen, oder löse den Standard-Balken aus externen Scripts aus."
icon: "spinner"
---

## Ersetzen/Deaktivieren

Wird ausgelöst, wenn der Fortschrittsbalken genutzt wird.

```lua Event
RegisterNetEvent("farming_creator:internalProgressBar", function(time, text)

end)
```

### Parameter

| Name   | Datentyp | Beschreibung                       |
| ------ | --------- | ---------------------------------- |
| `time` | integer   | Dauer des Fortschrittsbalkens in Sekunden   |
| `text` | string    | Beschreibungstext                   |

### Beispiel

```lua
-- In farming_creator/integrations/cl_integrations.lua
RegisterNetEvent("farming_creator:framework:ready", function()
    -- Deaktiviert den Standard-Fortschrittsbalken des Scripts (sonst gäbe es 2 Fortschrittsbalken)
    exports["farming_creator"]:disableScriptEvent("farming_creator:internalProgressBar")
end)

-- Beispiel, um den Fortschrittsbalken des Scripts durch einen externen zu ersetzen
RegisterNetEvent("farming_creator:internalProgressBar", function(time, text)
    -- Das Event, um deinen externen Fortschrittsbalken zu aktivieren
    TriggerEvent("external_progressbar:start", time, text)
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/cl_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>

## Nutzung in externen Scripts

Falls dir der Standard-Fortschrittsbalken des Scripts gefällt und du ihn in externen Scripts nutzen möchtest, ist dies das Event:

```lua
TriggerEvent("farming_creator:startProgressBar", timeInMS, text, hexColor)
```

### Parameter

| Name       | Datentyp | Beschreibung                                                                                            |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |
| `timeInMS` | integer   | Dauer des Fortschrittsbalkens in Millisekunden                                                              |
| `text`     | string    | Der Text, der mit dem Fortschrittsbalken angezeigt wird                                                         |
| `hexColor` | string    | Die Farbe des Fortschrittsbalkens als Hex-Code (Beispiel `#70f2b4`). Kann `nil` sein, um die Standardfarbe des Scripts zu nutzen |

### Beispiel

```lua
-- Dies erstellt einen Befehl, um einen roten Fortschrittsbalken anzuzeigen
-- /progressbar 5000 Hello
RegisterCommand("progressbar", function(playerId, args)
    TriggerEvent("farming_creator:startProgressBar", tonumber(args[1]), args[2], "#ff0000")
end)
```
