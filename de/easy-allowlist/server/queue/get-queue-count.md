---
title: "Queue-Anzahl abrufen"
description: "Ruft die Anzahl der Spieler ab, die sich aktuell in der Queue befinden."
icon: "hashtag"
---

Nutze den folgenden Export, wenn du **die Anzahl der Spieler, die sich aktuell in der Queue befinden**, abrufen möchtest.

```lua Export
-- Gibt eine Zahl zurück
exports["easy_allowlist"]:getQueueCount()
```

## Beispiel

```lua
RegisterCommand("queuecount", function(source, args)
    local queueCount = exports["easy_allowlist"]:getQueueCount()
    print("Queue count: " .. queueCount)
end, false)
```

<Note>
  Du kannst diesen Code in `sv_integrations.lua` des Scripts oder in jeder anderen server-seitigen Lua-Datei hinzufügen.
</Note>
