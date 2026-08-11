---
title: "Discord-Rollen-Queue-Priorität entfernen"
description: "Entfernt eine Queue-Priorität für eine Discord-Rolle."
icon: "arrow-down-short-wide"
---

Entfernt eine Queue-Priorität für eine Discord-Rolle.

<CodeGroup>

```lua Export
exports["easy_allowlist"]:removeDiscordRoleQueuePriority(discordRoleId)
```

```lua Example
local discordRoleId = "332962646660794880"
exports["easy_allowlist"]:removeDiscordRoleQueuePriority(discordRoleId)
```

</CodeGroup>

### Parameter

| Name            | Datentyp | Beschreibung      |
| ---------------- | --------- | ----------------- |
| `discordRoleId`  | string    | Die Discord-Rollen-ID |
