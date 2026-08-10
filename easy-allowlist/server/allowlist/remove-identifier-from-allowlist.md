---
title: "Remove identifier from allowlist"
description: "Remove an identifier from the allowlist."
icon: "user-minus"
---

Remove the allowlist for an identifier.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:removeAllowlistFromIdentifier(identifier)
```

```lua Example
exports["easy_allowlist"]:removeAllowlistFromIdentifier("steam:71002010c2f9c5d")
```

</CodeGroup>

### Parameters

| Name         | Data Type | Description                 |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | The player's main identifier |
