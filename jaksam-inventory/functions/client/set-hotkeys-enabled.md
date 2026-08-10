---
title: "Set hotkeys enabled"
description: "Enables or disables the hotkeys functionality (slots 1-5). Useful for example during minigames or cutscenes."
icon: "keyboard"
---

Enables or disables the hotkeys functionality (slots 1-5). Useful for example during minigames or cutscenes. Don't forget to re-enable the hotkeys when finished.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setHotkeysEnabled(enabled)
```

```lua Example
-- Disable the hotkeys
exports['jaksam_inventory']:setHotkeysEnabled(false)

-- Enable the hotkeys
exports['jaksam_inventory']:setHotkeysEnabled(true)

-- Disable hotkeys during a minigame
exports['jaksam_inventory']:setHotkeysEnabled(false)
-- ... minigame code ...
exports['jaksam_inventory']:setHotkeysEnabled(true)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `enabled` | boolean | If true, the hotkeys will be enabled and will work normally. If false, the hotkeys will be disabled and pressing 1-5 will be ignored |

### Return value

None.
