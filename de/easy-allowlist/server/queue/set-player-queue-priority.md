---
title: "Spieler-Queue-Priorität setzen"
description: "Setzt eine Queue-Priorität für eine online Spieler-ID."
icon: "arrow-up-short-wide"
---

Setzt eine Queue-Priorität für eine online Spieler-ID.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:setPlayerQueuePriority(playerId, priority)
```

```lua Example
local playerId = 61
exports["easy_allowlist"]:setPlayerQueuePriority(playerId, 15)
```

</CodeGroup>

### Parameter

| Name       | Datentyp | Beschreibung       |
| ---------- | --------- | -------------------- |
| `playerId` | integer   | Server-ID des Spielers   |
| `priority` | integer   | Queue-Priorität        |
