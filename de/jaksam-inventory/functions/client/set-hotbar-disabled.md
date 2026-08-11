---
title: "Set hotbar disabled"
description: "Aktiviert oder deaktiviert die Hotbar-Funktion. Nützlich z.B. während Minigames."
icon: "grip-lines"
---

Aktiviert oder deaktiviert die Hotbar-Funktion. Nützlich z.B. während Minigames. Vergiss nicht, die Hotbar danach wieder zu aktivieren.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setHotbarDisabled(disabled)
```

```lua Example
-- Hotbar deaktivieren
exports['jaksam_inventory']:setHotbarDisabled(true)

-- Hotbar aktivieren
exports['jaksam_inventory']:setHotbarDisabled(false)

-- Hotbar während einer Cutscene deaktivieren
exports['jaksam_inventory']:setHotbarDisabled(true)
-- ... Cutscene-Code ...
exports['jaksam_inventory']:setHotbarDisabled(false)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `disabled` | boolean | Bei true wird die Hotbar deaktiviert und `showHotbar()`-Aufrufe werden ignoriert. Bei false wird die Hotbar aktiviert und funktioniert normal |

### Rückgabewert

Keiner.
