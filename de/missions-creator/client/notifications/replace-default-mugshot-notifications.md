---
title: "Standard-Mugshot-Benachrichtigungen ersetzen"
description: "Ersetze die Benachrichtigung, die für die 'Mit Ped sprechen'-Aktion angezeigt wird (mit NPC-Gesicht)."
icon: "id-card"
---

Benachrichtigung, die bei der "Mit Ped sprechen"-Aktion angezeigt wird (Benachrichtigung mit NPC-Gesicht).

```lua Event
AddEventHandler("missions_creator:internalMugshotNotify", function(ped, title, message)

end)
```

### Parameter

| Name      | Datentyp | Beschreibung                   |
| --------- | --------- | -------------------------------- |
| `ped`     | integer   | Handle der Ped-Entität                |
| `title`   | string    | Titel der Benachrichtigung         |
| `message` | string    | Nachricht der Benachrichtigung       |

## Beispiel

```lua
RegisterNetEvent("missions_creator:framework:ready", function()
    -- Deaktiviert die Standard-Benachrichtigung des Scripts (sonst gäbe es 2 Benachrichtigungen)
    exports["missions_creator"]:disableScriptEvent("missions_creator:internalMugshotNotify")
end)

RegisterNetEvent("missions_creator:internalMugshotNotify", function(ped, title, message)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Platziere diesen Code in der Datei `jaksam_core/config/cl_config.lua`, am Ende der Datei in neuen Zeilen.
</Note>
