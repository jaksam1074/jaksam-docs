---
title: "Polizei alarmiert"
description: "Wird server-seitig ausgelöst, einmal pro Alarm, wenn die Polizei alarmiert wird."
icon: "siren-on"
---

Wird ausgelöst, wenn die Polizei server-seitig alarmiert wird (nur **1** Mal pro Alarm, statt bei jedem Spieler wie beim client-seitigen Event).

```lua Event
RegisterNetEvent("robberies_creator:alertedPolice", function(coords, message)

end)
```

### Parameter

| Name      | Datentyp | Beschreibung                                |
| --------- | --------- | -------------------------------------------- |
| `coords`  | vector3   | Koordinaten, an denen der Alarm ausgelöst wurde     |
| `message` | string    | Nachricht, die angezeigt werden würde               |

## Beispiel

```lua
RegisterNetEvent("robberies_creator:alertedPolice", function(coords, message)
    -- nur ein Beispiel, wird NICHT funktionieren
    TriggerClientEvent("news_script:heistAlert", -1, coords, message)
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
