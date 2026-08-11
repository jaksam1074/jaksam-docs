---
title: "Queue-Infos abrufen"
description: "Ruft die Daten der Spieler ab, die sich aktuell in der Queue befinden."
icon: "circle-info"
---

Nutze den folgenden Export, um die Daten der Spieler abzurufen, die sich aktuell in der Queue befinden (Nickname, Identifier, Priorität, usw.).

```lua Export
-- Gibt eine Table zurück
exports["easy_allowlist"]:getPlayersInQueue()
```

## Beispiel

```lua
RegisterCommand("queueinfo", function(source, args)
    local queueInfo = exports["easy_allowlist"]:getPlayersInQueue()
    print(json.encode(queueInfo, { indent = true }))
end, false)
```

<Note>
  Du kannst diesen Code in `sv_integrations.lua` des Scripts oder in jeder anderen server-seitigen Lua-Datei hinzufügen.
</Note>
