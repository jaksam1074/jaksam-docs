---
title: "Standard-Polizei-Alarm ersetzen"
description: "Ersetze das client-seitige Polizei-Alarm-Verhalten durch dein eigenes."
icon: "siren-on"
---

<Warning>
  Wird ausgelöst, wenn die Polizei alarmiert wird. Dies wird auf **jedem** Client eines Polizei-Spielers ausgelöst — falls du ein einzelnes Event suchst, sieh dir die server-seitige Kategorie an.
</Warning>

```lua Event
RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)

end)
```

### Parameter

| Name      | Datentyp | Beschreibung                     |
| --------- | --------- | ---------------------------------- |
| `coords`  | vector3   | Koordinaten, die an die Polizei gesendet werden       |
| `message` | string    | Die Nachricht, die der Cop sehen wird        |

## Beispiel

```lua
-- Deaktiviert den Standard-Polizei-Alarm
RegisterNetEvent("missions_creator:framework:ready", function()
    exports["missions_creator"]:disableScriptEvent("missions_creator:alertedPolice")
end)

RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)
    -- Do something
end)
```

<Note>
  Platziere diesen Code in der Datei `jaksam_core/config/cl_config.lua`, am Ende der Datei in neuen Zeilen.
</Note>
