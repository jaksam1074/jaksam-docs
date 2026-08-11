---
title: "Standard-Mugshot-Benachrichtigungen ersetzen"
description: "Ersetze die Benachrichtigung, die angezeigt wird, wenn ein Ped eine Droge beim NPC-Verkauf ablehnt."
icon: "id-card"
---

Benachrichtigung, die angezeigt wird, wenn ein Ped die Droge beim NPC-Verkauf ablehnt (Benachrichtigung mit dem Gesicht des Peds).

```lua Event
AddEventHandler("drugs_creator:internalMugshotNotify", function(ped, title, message)

end)
```

### Parameter

| Name      | Datentyp | Beschreibung                   |
| --------- | --------- | ---------------------------------- |
| `ped`     | integer   | Handle der Ped-Entität                     |
| `title`   | string    | Titel der Benachrichtigung               |
| `message` | string    | Nachricht der Benachrichtigung              |

## Beispiel

```lua
RegisterNetEvent("drugs_creator:framework:ready", function()
    -- Deaktiviert die Standard-Benachrichtigung des Scripts (sonst gäbe es 2 Benachrichtigungen)
    exports["drugs_creator"]:disableScriptEvent("drugs_creator:internalMugshotNotify")
end)

RegisterNetEvent("drugs_creator:internalMugshotNotify", function(ped, title, message)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/cl_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
