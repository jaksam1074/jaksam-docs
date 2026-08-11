---
title: "Set hotkeys enabled"
description: "Aktiviert oder deaktiviert die Hotkey-Funktion (Slots 1-5). Nützlich z.B. während Minigames oder Cutscenes."
icon: "keyboard"
---

Aktiviert oder deaktiviert die Hotkey-Funktion (Slots 1-5). Nützlich z.B. während Minigames oder Cutscenes. Vergiss nicht, die Hotkeys danach wieder zu aktivieren.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setHotkeysEnabled(enabled)
```

```lua Example
-- Hotkeys deaktivieren
exports['jaksam_inventory']:setHotkeysEnabled(false)

-- Hotkeys aktivieren
exports['jaksam_inventory']:setHotkeysEnabled(true)

-- Hotkeys während eines Minigames deaktivieren
exports['jaksam_inventory']:setHotkeysEnabled(false)
-- ... Minigame-Code ...
exports['jaksam_inventory']:setHotkeysEnabled(true)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `enabled` | boolean | Bei true werden die Hotkeys aktiviert und funktionieren normal. Bei false werden die Hotkeys deaktiviert und das Drücken von 1-5 wird ignoriert |

### Rückgabewert

Keiner.
