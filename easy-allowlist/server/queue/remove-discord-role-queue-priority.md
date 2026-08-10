---
title: "Remove Discord role queue priority"
description: "Remove a queue priority for a Discord role."
icon: "arrow-down-short-wide"
---

Remove a queue priority for a Discord role.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:removeDiscordRoleQueuePriority(discordRoleId)
```

```lua Example
local discordRoleId = "332962646660794880"
exports["easy_allowlist"]:removeDiscordRoleQueuePriority(discordRoleId)
```

</CodeGroup>

### Parameters

| Name            | Data Type | Description      |
| ---------------- | --------- | ----------------- |
| `discordRoleId`  | string    | The Discord role ID |
