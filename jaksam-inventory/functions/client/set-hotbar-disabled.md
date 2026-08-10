---
title: "Set hotbar disabled"
description: "Enables or disables the hotbar functionality. Useful for example during minigames."
icon: "grip-lines"
---

Enables or disables the hotbar functionality. Useful for example during minigames. Don't forget to re-enable the hotbar when finished.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setHotbarDisabled(disabled)
```

```lua Example
-- Disable the hotbar
exports['jaksam_inventory']:setHotbarDisabled(true)

-- Enable the hotbar
exports['jaksam_inventory']:setHotbarDisabled(false)

-- Disable hotbar during a cutscene
exports['jaksam_inventory']:setHotbarDisabled(true)
-- ... cutscene code ...
exports['jaksam_inventory']:setHotbarDisabled(false)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `disabled` | boolean | If true, the hotbar will be disabled and `showHotbar()` calls will be ignored. If false, the hotbar will be enabled and will work normally |

### Return value

None.
