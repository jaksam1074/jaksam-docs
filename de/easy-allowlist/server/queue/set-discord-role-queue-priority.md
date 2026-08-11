---
title: "Discord-Rollen-Queue-Priorität setzen"
description: "Setzt eine Queue-Priorität für eine Discord-Rolle."
icon: "arrow-up-short-wide"
---

Setzt eine Queue-Priorität für eine Discord-Rollen-ID.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:setDiscordRolePriority(discordRoleId, priority)
```

```lua Example
local discordRoleId = "332962646660794880"
exports["easy_allowlist"]:setDiscordRolePriority(discordRoleId, 30)
```

</CodeGroup>

### Parameter

| Name            | Datentyp | Beschreibung       |
| ---------------- | --------- | ------------------- |
| `discordRoleId`  | string    | Discord-Rollen-ID     |
| `priority`       | integer   | Queue-Priorität      |
