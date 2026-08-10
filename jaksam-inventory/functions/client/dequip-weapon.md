---
title: "Dequip weapon"
description: "Dequips the currently equipped weapon."
icon: "gun"
---

Dequips the currently equipped weapon.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:dequipWeapon(skipSync)
```

```lua Example
-- Dequip weapon
exports['jaksam_inventory']:dequipWeapon()

-- Dequip weapon without syncing the ammo to the server
exports['jaksam_inventory']:dequipWeapon(true)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `skipSync` | boolean | If true, the weapon will be dequipped without syncing the ammo to the server |

### Return value

None. Dequips the currently equipped weapon.
