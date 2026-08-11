---
title: "Polizei alarmiert"
description: "Wird server-seitig ausgelöst, einmal pro Alarm, wenn die Polizei alarmiert wird."
icon: "siren-on"
---

<Warning>
  Wird ausgelöst, wenn die Polizei server-seitig alarmiert wird (nur **1** Mal pro Alarm, statt bei jedem Spieler wie beim client-seitigen Event).
</Warning>

```lua Event
RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)

end)
```

### Parameter

| Name      | Datentyp | Beschreibung                                |
| --------- | --------- | -------------------------------------------- |
| `coords`  | vector3   | Koordinaten, an denen der Alarm ausgelöst wurde     |
| `message` | string    | Nachricht, die angezeigt werden würde               |

## Beispiel

```lua
RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)
    -- nur ein Beispiel, wird NICHT funktionieren
    TriggerClientEvent("news_script:heistAlert", -1, coords, message)
end)
```

<Note>
  Platziere diesen Code in der Datei `jaksam_core/config/sv_config.lua`, am Ende der Datei in neuen Zeilen.
</Note>
