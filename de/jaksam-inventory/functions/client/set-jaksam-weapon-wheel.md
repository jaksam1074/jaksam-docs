---
title: "Set jaksam weapon wheel"
description: "Aktiviert oder deaktiviert das eigene radiale Waffenrad von jaksam zur Laufzeit."
icon: "circle-dot"
---

Aktiviert oder deaktiviert das eigene radiale Waffenrad von jaksam zur Laufzeit. Nützlich, wenn Spieler in bestimmten Situationen (Cutscenes, Minigames usw.) nicht über das Radialrad die Waffe wechseln können sollen.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setJaksamWeaponWheel(state)
```

```lua Example
-- jaksam-Waffenrad während einer Cutscene deaktivieren
exports['jaksam_inventory']:setJaksamWeaponWheel(false)
-- ... Cutscene-Code ...
exports['jaksam_inventory']:setJaksamWeaponWheel(true) -- Danach wieder aktivieren
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `state` | boolean \| nil | Bei true wird das radiale jaksam-Waffenrad aktiviert. Bei false wird es deaktiviert (schließt es sofort, falls offen). Bei nil wird der aktuelle interne Zustand verwendet |

### Rückgabewert

Keiner.
