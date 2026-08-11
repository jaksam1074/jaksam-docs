---
title: "Waffe aus Armory entfernen"
description: "Entferne eine Waffe aus einem bestimmten Armory-Marker anhand ihrer Waffen-ID."
icon: "gun"
---

Entfernt eine Waffe aus einer Marker-ID für einen bestimmten Spieler.

<CodeGroup>

```lua Export
exports["jobs_creator"]:removeWeaponFromArmory(markerId, weaponId)
```

```lua Beispiel
local markerId = 15
local weaponId = 356
local success = exports["jobs_creator"]:removeWeaponFromArmory(markerId, weaponId)
print(success)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `markerId` | integer | Die Marker-ID |
| `weaponId` | integer | Waffen-ID in der Datenbank, einsehbar über `exports["jobs_creator"]:getAllArmoryWeapons(markerId)` |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isSuccessful` | boolean | Ob die Waffe entfernt wurde oder nicht |
