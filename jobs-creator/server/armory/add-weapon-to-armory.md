---
title: "Add weapon to armory"
description: "Add a weapon to a specific armory marker for a given player."
icon: "gun"
---

Add a weapon to a marker ID for a specific player.

<CodeGroup>

```lua Export
exports["jobs_creator"]:addWeaponToArmory(markerId, playerIdentifier, weaponName, weaponAmmo, weaponComponents, weaponTintIndex)
```

```lua Example
local success = exports["jobs_creator"]:addWeaponToArmory(3, "2570e6efd3671584d7ed05a45cbf4156f782wwac", "WEAPON_PISTOL", 5, {}, 1)
print(success)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `markerId` | integer | The marker ID |
| `playerIdentifier` | string | Player identifier |
| `weaponName` | string | Weapon name |
| `weaponAmmo` | integer | Ammo count |
| `weaponComponents` | table | Table of weapon components |
| `weaponTintIndex` | integer | Weapon tint index |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `isSuccessful` | boolean | Whether the weapon was added or not |