---
title: "Standard-Polizei-Alarm ersetzen"
description: "Ersetze das client-seitige Polizei-Alarm-Verhalten durch dein eigenes."
icon: "siren-on"
---

<Warning>
  Wird ausgelöst, wenn die Polizei alarmiert wird. Dies wird auf **jedem** Client eines Polizei-Spielers ausgelöst — falls du ein einzelnes Event suchst, sieh dir die server-seitige Kategorie an.
</Warning>

```lua Event
RegisterNetEvent("vehicles_keys:alertedPolice", function(coords, message)

end)
```

### Parameter

| Name      | Datentyp | Beschreibung                                |
| --------- | --------- | -------------------------------------------- |
| `coords`  | vector3   | Koordinaten, an denen der Alarm ausgelöst wurde     |
| `message` | string    | Die Nachricht, die der Cop sehen wird                  |

## Beispiel

```lua
-- Deaktiviert den Standard-Polizei-Alarm
RegisterNetEvent("vehicles_keys:framework:ready", function()
    exports["vehicles_keys"]:disableScriptEvent("vehicles_keys:alertedPolice")
end)

RegisterNetEvent("vehicles_keys:alertedPolice", function(coords, message)
    -- Do something
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/cl_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
