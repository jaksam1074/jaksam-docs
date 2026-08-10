---
title: "Set identifier queue priority"
description: "Set a queue priority for an identifier."
icon: "arrow-up-short-wide"
---

Set an identifier's queue priority.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:setIdentifierQueuePriority(identifier, priority)
```

```lua Example
exports["easy_allowlist"]:setIdentifierQueuePriority("steam:71002010c2f9c5d", 15)
```

</CodeGroup>

### Parameters

| Name         | Data Type | Description                |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | The player's main identifier |
| `priority`   | integer   | Queue priority               |
