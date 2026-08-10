---
title: "Add identifier to allowlist"
description: "Add an identifier to the allowlist."
icon: "user-plus"
---

Add the allowlist for an identifier.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:addIdentifierToAllowlist(identifier)
```

```lua Example
exports["easy_allowlist"]:addIdentifierToAllowlist("steam:71002010c2f9c5d")
```

</CodeGroup>

### Parameters

| Name         | Data Type | Description                 |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | The player's main identifier |
