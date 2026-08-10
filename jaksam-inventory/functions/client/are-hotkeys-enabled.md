---
title: "Are hotkeys enabled"
description: "Returns whether the hotkeys are currently enabled or disabled."
icon: "keyboard"
---

Returns whether the hotkeys are currently enabled or disabled.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:areHotkeysEnabled()
```

```lua Example
-- Check if hotkeys are enabled
local enabled = exports['jaksam_inventory']:areHotkeysEnabled()

if enabled then
    print('Hotkeys are enabled')
else
    print('Hotkeys are disabled')
end

-- Toggle hotkeys
local currentState = exports['jaksam_inventory']:areHotkeysEnabled()
exports['jaksam_inventory']:setHotkeysEnabled(not currentState)
```

</CodeGroup>

### Parameters

None.

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `enabled` | boolean | True if hotkeys are enabled, false if disabled |
