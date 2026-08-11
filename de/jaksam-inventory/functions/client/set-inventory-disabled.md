---
title: "Set inventory disabled"
description: "Deaktiviert oder aktiviert das Öffnen des Inventars vollständig, blockiert Hotkeys, Keybinds und direkte Export-/Event-Aufrufe."
icon: "ban"
---

Deaktiviert oder aktiviert das Öffnen des Inventars vollständig. Bei Deaktivierung werden alle Inventar-Interaktionen blockiert: Hotkeys, Keybinds und direkte Export-/Event-Aufrufe. Ist das Inventar beim Deaktivieren gerade geöffnet, wird es geschlossen und die Waffe automatisch abgelegt.

Nützlich für Cutscenes, Minigames, Progress-Bars oder jedes Szenario, in dem der Spieler das Inventar nicht öffnen können soll.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setInventoryDisabled(disabled)
```

```lua Example
-- Inventar während einer Cutscene deaktivieren
exports['jaksam_inventory']:setInventoryDisabled(true)
-- ... Cutscene-Code ...
exports['jaksam_inventory']:setInventoryDisabled(false)

-- Inventar während einer Progress-Bar deaktivieren
exports['jaksam_inventory']:setInventoryDisabled(true)
-- ... Progress-Bar-Logik ...
exports['jaksam_inventory']:setInventoryDisabled(false)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `disabled` | boolean | Bei true wird das Öffnen des Inventars vollständig blockiert. Bei false wird das Öffnen wieder aktiviert |

### Rückgabewert

Keiner.

### Hinweise

**ox_inventory-Kompatibilität:** Falls du von ox_inventory migrierst, ersetzt dieser Export das `invBusy`-State-Bag-Muster. Scripts, die `LocalPlayer.state:set('invBusy', true, true)` setzen, funktionieren weiterhin automatisch, jaksam_inventory hört auf `invBusy`-State-Bag-Änderungen und bildet sie auf das gleiche interne Flag ab.

```lua
-- ox_inventory-Muster (funktioniert weiterhin mit jaksam_inventory)
LocalPlayer.state:set('invBusy', true, true)

-- Nativer jaksam_inventory-Export (empfohlen)
exports['jaksam_inventory']:setInventoryDisabled(true)
```
