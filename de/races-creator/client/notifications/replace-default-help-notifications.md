---
title: "Standard-Hilfe-Benachrichtigungen ersetzen"
description: "Ersetze die Standard-'Press E to ...'-Hilfe-Benachrichtigung durch deine eigene."
icon: "circle-info"
---

Wird genutzt, um den üblichen `Press E to ...`-Text oben links am Bildschirm des Spielers anzuzeigen.

```lua Export
exports["races_creator"]:replaceShowHelpNotification(customFunction)
```

### Parameter

| Name             | Datentyp | Beschreibung                                                                                                    |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------------------- |
| `customFunction` | function  | Eine Funktion, die die Standard-Methode `ESX.ShowHelpNotification` ersetzt. **Benötigt** den message-Parameter und wird jeden Frame aufgerufen |

## Beispiel

```lua
local function myCustomHelpNotification(message)
    -- Passe die Funktion an deine Bedürfnisse an
    print(message)

    ExternalScript.showHelpNotification(message)
end

RegisterNetEvent("races_creator:framework:ready", function()
    -- Dies ersetzt die Basisfunktion durch die gewünschte
    exports["races_creator"]:replaceShowHelpNotification(myCustomHelpNotification)
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/cl_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
