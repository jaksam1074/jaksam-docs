---
title: "Set player queue priority"
description: "Set a queue priority for an online player ID."
icon: "arrow-up-short-wide"
---

Set a queue priority for an online player ID.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:setPlayerQueuePriority(playerId, priority)
```

```lua Example
local playerId = 61
exports["easy_allowlist"]:setPlayerQueuePriority(playerId, 15)
```

</CodeGroup>

### Parameters

| Name       | Data Type | Description       |
| ---------- | --------- | -------------------- |
| `playerId` | integer   | Player's server ID   |
| `priority` | integer   | Queue priority        |
