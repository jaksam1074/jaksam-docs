---
title: "Set weapon wheel"
description: "Enables or disables the default GTA5 weapon wheel and related weapon settings. Useful for minigames."
icon: "circle-dot"
---

Enables or disables the weapon wheel and related weapon settings. Useful for minigames where you want the GTA 5 weapon wheel.

<Warning>
  This function will prevent using weapons from the inventory, it's mainly for FFA minigames.
</Warning>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setWeaponWheel(state)
```

```lua Example
-- Disable GTA5 weapon wheel (default jaksam_inventory mode)
exports['jaksam_inventory']:setWeaponWheel(false)

-- Enable GTA5 weapon wheel (enable only for minigames)
exports['jaksam_inventory']:setWeaponWheel(true)

-- Enable default GTA 5 weapon wheel during FFA minigame
exports['jaksam_inventory']:setWeaponWheel(true)
-- ... minigame code ...
exports['jaksam_inventory']:setWeaponWheel(false) -- Disable GTA5 wheel again, returning to normal jaksam_inventory
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `state` | boolean \| nil | If true, the default GTA5 weapon wheel will be enabled and weapons WON'T be handled by jaksam inventory. If false, the default GTA5 weapon wheel will be disabled and weapons WILL be handled by jaksam inventory. If nil, uses the current internal state |

### Return value

None. Automatically dequips the current weapon when called.
