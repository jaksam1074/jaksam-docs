---
title: "Identifier zur Allowlist hinzufügen"
description: "Füge einen Identifier zur Allowlist hinzu."
icon: "user-plus"
---

Fügt die Allowlist für einen Identifier hinzu.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:addIdentifierToAllowlist(identifier)
```

```lua Example
exports["easy_allowlist"]:addIdentifierToAllowlist("steam:71002010c2f9c5d")
```

</CodeGroup>

### Parameter

| Name         | Datentyp | Beschreibung                 |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | Der Haupt-Identifier des Spielers |
