---
title: "Dequip weapon"
description: "Legt die aktuell ausgerüstete Waffe ab."
icon: "gun"
---

Legt die aktuell ausgerüstete Waffe ab.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:dequipWeapon(skipSync)
```

```lua Example
-- Waffe ablegen
exports['jaksam_inventory']:dequipWeapon()

-- Waffe ablegen, ohne die Munition mit dem Server zu synchronisieren
exports['jaksam_inventory']:dequipWeapon(true)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `skipSync` | boolean | Bei true wird die Waffe abgelegt, ohne die Munition mit dem Server zu synchronisieren |

### Rückgabewert

Keiner. Legt die aktuell ausgerüstete Waffe ab.
