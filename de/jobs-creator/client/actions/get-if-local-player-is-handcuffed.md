---
title: "Prüfen, ob der lokale Spieler gefesselt ist"
description: "Prüfe, ob der lokale Spieler aktuell gefesselt ist."
icon: "handcuffs"
---

Gibt zurück, ob der **lokale** Client/Spieler gefesselt ist.

<CodeGroup>

```lua Export
exports["jobs_creator"]:isPlayerHandcuffed()
```

```lua Beispiel
-- Dieser Code prüft fortlaufend, ob der lokale (eigene) Spieler gefesselt ist
-- Falls ja, werden bestimmte Controls deaktiviert
Citizen.CreateThread(function()
    while true do
        Citizen.Wait(0)

        if(exports["jobs_creator"]:isPlayerHandcuffed())then
            DisableControlAction(0, 22, true) -- Springen deaktivieren
        end
    end
end)
```

</CodeGroup>

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isHandcuffed` | boolean | `true`, wenn der Spieler gefesselt ist, `false`, wenn der Spieler **nicht** gefesselt ist |

### Wo füge ich den Code ein?

Du kannst den Code in jede beliebige Client-Datei deiner Scripts einfügen.
