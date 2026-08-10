---
title: "Remove identifier queue priority"
description: "Remove a queue priority for an identifier."
icon: "arrow-down-short-wide"
---

Remove a queue priority for an identifier.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:removeIdentifierQueuePriority(identifier)
```

```lua Example
exports["easy_allowlist"]:removeIdentifierQueuePriority("steam:71002010c2f9c5d")
```

</CodeGroup>

### Parameters

| Name         | Data Type | Description                 |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | The player's main identifier |
