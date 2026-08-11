---
title: "Datenbank aktualisieren"
description: "Aktualisiert Doors Creator, nachdem manuell etwas in der Datenbank erstellt wurde."
icon: "rotate"
---

Nützlich, um Doors Creator zu aktualisieren, nachdem du manuell etwas in der Datenbank erstellt hast.

```lua Export
exports["doors_creator"]:refreshDatabase()
```

## Beispiel

```lua
RegisterCommand("refreshDoorsCreator", function(playerId)
    -- Nur die Server-Konsole kann den Befehl nutzen
    if(playerId and playerId > 0) then return end

    exports["doors_creator"]:refreshDatabase()
end)
```
