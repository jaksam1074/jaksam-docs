---
title: "Fortschrittsbalken"
description: "Ersetze den Standard-Fortschrittsbalken durch deinen eigenen, oder löse den Standard-Balken aus externen Scripts aus."
icon: "spinner"
---

## Wie ersetze ich ihn?

Du kannst ein Robberies Creator [Modul](/de/robberies-creator/modules) nutzen, wenn du deinen eigenen Fortschrittsbalken verwenden möchtest.

## Nutzung in externen Scripts

Falls dir der Standard-Fortschrittsbalken des Scripts gefällt und du ihn in externen Scripts nutzen möchtest, ist dies das Event:

```lua
TriggerEvent("robberies_creator:startProgressBar", timeInMS, text, hexColor)
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
    TriggerEvent("robberies_creator:startProgressBar", tonumber(args[1]), args[2], "#ff0000")
end)
```
