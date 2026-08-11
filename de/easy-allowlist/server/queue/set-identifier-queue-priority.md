---
title: "Identifier-Queue-Priorität setzen"
description: "Setzt eine Queue-Priorität für einen Identifier."
icon: "arrow-up-short-wide"
---

Setzt die Queue-Priorität eines Identifiers.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:setIdentifierQueuePriority(identifier, priority)
```

```lua Example
exports["easy_allowlist"]:setIdentifierQueuePriority("steam:71002010c2f9c5d", 15)
```

</CodeGroup>

### Parameter

| Name         | Datentyp | Beschreibung                |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | Der Haupt-Identifier des Spielers |
| `priority`   | integer   | Queue-Priorität               |
