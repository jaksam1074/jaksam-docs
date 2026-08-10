---
title: "Set inventory disabled"
description: "Completely disables or re-enables inventory opening, blocking hotkeys, keybinds, and direct export/event calls."
icon: "ban"
---

Completely disables or re-enables inventory opening. When disabled, all inventory interactions are blocked: hotkeys, keybinds, and direct export/event calls. If the inventory is currently open when disabling, it will be closed and the weapon will be dequipped automatically.

This is useful for cutscenes, minigames, progress bars, or any scenario where the player should not be able to open the inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setInventoryDisabled(disabled)
```

```lua Example
-- Disable inventory during a cutscene
exports['jaksam_inventory']:setInventoryDisabled(true)
-- ... cutscene code ...
exports['jaksam_inventory']:setInventoryDisabled(false)

-- Disable inventory during a progress bar
exports['jaksam_inventory']:setInventoryDisabled(true)
-- ... progress bar logic ...
exports['jaksam_inventory']:setInventoryDisabled(false)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `disabled` | boolean | If true, inventory opening is completely blocked. If false, inventory opening is re-enabled |

### Return value

None.

### Notes

**ox_inventory compatibility:** If you are migrating from ox_inventory, this export replaces the `invBusy` state bag pattern. Scripts that set `LocalPlayer.state:set('invBusy', true, true)` will continue to work automatically, jaksam_inventory listens for `invBusy` state bag changes and maps them to the same internal flag.

```lua
-- ox_inventory pattern (still works with jaksam_inventory)
LocalPlayer.state:set('invBusy', true, true)

-- jaksam_inventory native export (recommended)
exports['jaksam_inventory']:setInventoryDisabled(true)
```
