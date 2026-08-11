---
title: "Waffe zur Armory hinzufügen"
description: "Füge einem bestimmten Armory-Marker eine Waffe für einen bestimmten Spieler hinzu."
icon: "gun"
---

Fügt einer Marker-ID eine Waffe für einen bestimmten Spieler hinzu.

<CodeGroup>

```lua Export
exports["jobs_creator"]:addWeaponToArmory(markerId, playerIdentifier, weaponName, weaponAmmo, weaponComponents, weaponTintIndex)
```

```lua Beispiel
local success = exports["jobs_creator"]:addWeaponToArmory(3, "2570e6efd3671584d7ed05a45cbf4156f782wwac", "WEAPON_PISTOL", 5, {}, 1)
print(success)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `markerId` | integer | Die Marker-ID |
| `playerIdentifier` | string | Spieler-Identifier |
| `weaponName` | string | Waffenname |
| `weaponAmmo` | integer | Munitionsanzahl |
| `weaponComponents` | table | Tabelle der Waffenkomponenten |
| `weaponTintIndex` | integer | Waffen-Tint-Index |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isSuccessful` | boolean | Ob die Waffe hinzugefügt wurde oder nicht |
