---
title: "Standard-Benachrichtigungen ersetzen"
description: "Nutze ein eigenes Benachrichtigungssystem anstelle des Standard-Systems, indem du auf das notify-Event hörst."
icon: "bell"
---

Wird ausgelöst, nachdem der Spieler client-seitig benachrichtigt wurde.

```lua Event
AddEventHandler("doors_creator:notify", function(message, uncoloredMessage)

end)
```

### Parameter

| Name               | Datentyp | Beschreibung                                                |
| ------------------ | --------- | ------------------------------------------------------------ |
| `message`          | string    | Nachricht der Benachrichtigung                                  |
| `uncoloredMessage` | string    | Nachricht der Benachrichtigung, aber ohne `~r~`, `~g~`, usw.   |

## Beispiel

```lua
RegisterNetEvent("doors_creator:framework:ready", function()
    -- Deaktiviert die Standard-Benachrichtigung des Scripts (sonst gäbe es 2 Benachrichtigungen)
    exports["doors_creator"]:disableScriptEvent("doors_creator:notify")
end)

RegisterNetEvent("doors_creator:notify", function(message, uncoloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/cl_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
