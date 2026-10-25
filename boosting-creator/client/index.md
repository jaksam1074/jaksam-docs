---
title: "Client"
description: "Client-side exports of Boosting Creator: replace the help notification, use the skill check from your own scripts."
icon: "laptop"
---

## Replace the help notification

The `Press E to ...` texts use the native help notification, or the **Text UI** [module](/boosting-creator/modules) you choose in the settings. To draw them yourself:

```lua
exports["boosting_creator"]:replaceShowHelpNotification(function(message)
    -- show message with your own UI
end)
```

The function is called every frame while the text should be on screen.

## Skill check

The skill check bar of the script can be used by other scripts.

```lua
local success = exports["boosting_creator"]:skillcheck(difficulty)
```

| Parameter | Type | Description |
| --- | --- | --- |
| `difficulty` | `number` | 1 to 3 |
| `speed` | `number` (optional) | Speed of the moving marker, overrides the difficulty |
| `positiveBars` | `number` (optional) | Size of the zone to hit, overrides the difficulty |

Returns `true` on success, `false` on failure or when another skill check is already open. It waits until the player is done.

To close an open skill check (it returns `false`):

```lua
exports["boosting_creator"]:cancelSkillcheck()
```

## Notifications, progress bar and dispatch

They are replaced with [modules](/boosting-creator/modules), not with exports.

## Custom minigames

See [Add your own minigame](/boosting-creator/guides/minigames#add-your-own-minigame).
