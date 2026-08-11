---
title: "Standard-Benachrichtigungen ersetzen"
description: "Nutze ein eigenes Benachrichtigungssystem anstelle des Standard-Systems, indem du auf das notify-Event hörst."
icon: "bell"
---

Wird ausgelöst, nachdem der Spieler client-seitig benachrichtigt wurde.

```lua Event
AddEventHandler("dealerships_creator:notify", function(message, coloredMessage)

end)
```

### Parameter

| Name              | Datentyp | Beschreibung                                              |
| ------------------ | --------- | ----------------------------------------------------------- |
| `message`          | string    | Nachricht der Benachrichtigung                                  |
| `coloredMessage`   | string    | Nachricht der Benachrichtigung, aber mit `~r~`, `~g~`, usw.       |

## Beispiel

```lua
RegisterNetEvent("dealerships_creator:framework:ready", function()
    -- Deaktiviert die Standard-Benachrichtigung des Scripts (sonst gäbe es 2 Benachrichtigungen)
    exports["dealerships_creator"]:disableScriptEvent("dealerships_creator:notify")
end)

RegisterNetEvent("dealerships_creator:notify", function(message, coloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/cl_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
