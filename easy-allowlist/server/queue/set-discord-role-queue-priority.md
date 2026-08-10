---
title: "Set Discord role queue priority"
description: "Set a queue priority for a Discord role."
icon: "arrow-up-short-wide"
---

Set a queue priority for a Discord role ID.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:setDiscordRolePriority(discordRoleId, priority)
```

```lua Example
local discordRoleId = "332962646660794880"
exports["easy_allowlist"]:setDiscordRolePriority(discordRoleId, 30)
```

</CodeGroup>

### Parameters

| Name            | Data Type | Description       |
| ---------------- | --------- | ------------------- |
| `discordRoleId`  | string    | Discord role ID     |
| `priority`       | integer   | Queue priority      |
