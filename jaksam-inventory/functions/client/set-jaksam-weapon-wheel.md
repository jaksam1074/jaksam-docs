---
title: "Set jaksam weapon wheel"
description: "Enables or disables the jaksam custom radial weapon wheel at runtime."
icon: "circle-dot"
---

Enables or disables the jaksam custom radial weapon wheel at runtime. Useful when you need to prevent players from switching weapons via the radial wheel during specific scenarios (cutscenes, minigames, etc.).

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setJaksamWeaponWheel(state)
```

```lua Example
-- Disable jaksam weapon wheel during a cutscene
exports['jaksam_inventory']:setJaksamWeaponWheel(false)
-- ... cutscene code ...
exports['jaksam_inventory']:setJaksamWeaponWheel(true) -- Re-enable after
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `state` | boolean \| nil | If true, the jaksam radial weapon wheel is enabled. If false, the jaksam radial weapon wheel is disabled (closes it immediately if open). If nil, uses the current internal state |

### Return value

None.
