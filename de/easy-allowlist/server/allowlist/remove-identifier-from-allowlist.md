---
title: "Identifier von Allowlist entfernen"
description: "Entferne einen Identifier von der Allowlist."
icon: "user-minus"
---

Entfernt die Allowlist für einen Identifier.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:removeAllowlistFromIdentifier(identifier)
```

```lua Example
exports["easy_allowlist"]:removeAllowlistFromIdentifier("steam:71002010c2f9c5d")
```

</CodeGroup>

### Parameter

| Name         | Datentyp | Beschreibung                 |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | Der Haupt-Identifier des Spielers |
