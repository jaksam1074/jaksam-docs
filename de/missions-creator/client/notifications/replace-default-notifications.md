---
title: "Standard-Benachrichtigungen ersetzen"
description: "Nutze ein eigenes Benachrichtigungssystem anstelle des Standard-Systems, indem du auf das notify-Event hörst."
icon: "bell"
---

Wird ausgelöst, nachdem der Spieler client-seitig benachrichtigt wurde.

```lua Event
AddEventHandler("missions_creator:notify", function(message, coloredMessage)

end)
```

### Parameter

| Name              | Datentyp | Beschreibung                                                |
| ----------------- | --------- | ------------------------------------------------------------ |
| `message`         | string    | Nachricht der Benachrichtigung, aber ohne `~r~`, `~g~`, usw.   |
| `coloredMessage`  | string    | Nachricht der Benachrichtigung                                  |

## Beispiel

```lua
RegisterNetEvent("missions_creator:framework:ready", function()
    -- Deaktiviert die Standard-Benachrichtigung des Scripts (sonst gäbe es 2 Benachrichtigungen)
    exports["missions_creator"]:disableScriptEvent("missions_creator:notify")
end)

RegisterNetEvent("missions_creator:notify", function(message, coloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

<Note>
  Platziere diesen Code in der Datei `jaksam_core/config/cl_config.lua`, am Ende der Datei in neuen Zeilen.
</Note>
