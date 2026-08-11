---
title: "Identifier-Queue-Priorität entfernen"
description: "Entfernt eine Queue-Priorität für einen Identifier."
icon: "arrow-down-short-wide"
---

Entfernt eine Queue-Priorität für einen Identifier.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:removeIdentifierQueuePriority(identifier)
```

```lua Example
exports["easy_allowlist"]:removeIdentifierQueuePriority("steam:71002010c2f9c5d")
```

</CodeGroup>

### Parameter

| Name         | Datentyp | Beschreibung                 |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | Der Haupt-Identifier des Spielers |
