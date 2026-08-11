---
title: "Fortschrittsbalken"
description: "Ersetze den Standard-Fortschrittsbalken durch deinen eigenen, oder verwende den eingebauten in externen Scripts."
icon: "spinner"
---

## So ersetzt du ihn

Du kannst ein Jobs-Creator-[Modul](/de/jobs-creator/modules) verwenden, wenn du deinen eigenen Fortschrittsbalken nutzen möchtest.

<Steps>
  <Step title="Zum Modules-Ordner navigieren">
    Gehe zum Ordner `jobs_creator/_modules`.
  </Step>
  <Step title="Den Progressbar-Modultyp finden">
    Suche das vorhandene Modul vom Typ **progressbar** als Vorlage.
  </Step>
  <Step title="Das Modul duplizieren">
    Kopiere das vorhandene Progressbar-Modul und füge es im gleichen Ordner ein.
  </Step>
  <Step title="Die Kopie umbenennen">
    Benenne die eingefügte Kopie passend zu deiner Integration um (z.B. `my_progressbar.lua`).
  </Step>
  <Step title="Die Datei öffnen">
    Öffne die neu umbenannte Datei.
  </Step>
  <Step title="Die Events anpassen">
    Bearbeite den Inhalt der Datei, sodass sie die Events/Exports deines eigenen Fortschrittsbalken-Scripts anstelle der Standardwerte aufruft.
  </Step>
  <Step title="Das Modul ingame auswählen">
    Öffne das `/jobscreator`-Menü, gehe zu den Einstellungen und wähle dein neues Modul für den Job aus.
  </Step>
</Steps>

## Verwendung in externen Scripts

Wenn dir der Standard-Fortschrittsbalken des Scripts gefällt und du ihn in externen Scripts verwenden möchtest, ist dies das Event:

<CodeGroup>

```lua Event
TriggerEvent("jobs_creator:startProgressBar", timeInMS, text, hexColor)
```

```lua Beispiel
-- Erstellt einen Befehl, um einen roten Fortschrittsbalken anzuzeigen
-- /progressbar 5000 Hello
RegisterCommand("progressbar", function(playerId, args)
    TriggerEvent("jobs_creator:startProgressBar", tonumber(args[1]), args[2], "#ff0000")
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `timeInMS` | integer | Dauer des Fortschrittsbalkens in Millisekunden |
| `text` | string | Der Text, der zusammen mit dem Fortschrittsbalken angezeigt wird |
| `hexColor` | string | Die Farbe des Fortschrittsbalkens als Hex-Code (Beispiel `#70f2b4`). Kann `nil` sein, um die Standardfarbe des Scripts zu verwenden |
