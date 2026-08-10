---
title: "Remove weapon from armory"
description: "Remove a weapon from a specific armory marker by its weapon ID."
icon: "gun"
---

Remove a weapon from a marker ID for a specific player.

<CodeGroup>

```lua Export
exports["jobs_creator"]:removeWeaponFromArmory(markerId, weaponId)
```

```lua Example
local markerId = 15
local weaponId = 356
local success = exports["jobs_creator"]:removeWeaponFromArmory(markerId, weaponId)
print(success)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `markerId` | integer | The marker ID |
| `weaponId` | integer | Weapon ID in the database, can be seen in `exports["jobs_creator"]:getAllArmoryWeapons(markerId)` |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `isSuccessful` | boolean | Whether the weapon was removed or not |