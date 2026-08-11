---
title: "Are hotkeys enabled"
description: "Gibt zurück, ob die Hotkeys aktuell aktiviert oder deaktiviert sind."
icon: "keyboard"
---

Gibt zurück, ob die Hotkeys aktuell aktiviert oder deaktiviert sind.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:areHotkeysEnabled()
```

```lua Example
-- Prüfen, ob Hotkeys aktiviert sind
local enabled = exports['jaksam_inventory']:areHotkeysEnabled()

if enabled then
    print('Hotkeys are enabled')
else
    print('Hotkeys are disabled')
end

-- Hotkeys umschalten
local currentState = exports['jaksam_inventory']:areHotkeysEnabled()
exports['jaksam_inventory']:setHotkeysEnabled(not currentState)
```

</CodeGroup>

### Parameter

Keine.

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `enabled` | boolean | True, falls Hotkeys aktiviert sind, false falls deaktiviert |
