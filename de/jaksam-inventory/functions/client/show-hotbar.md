---
title: "Show hotbar"
description: "Zeigt die Hotbar-UI mit den ersten 5 Slots des Inventars des Spielers."
icon: "grip"
---

Zeigt die Hotbar-UI mit den ersten 5 Slots des Inventars des Spielers.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:showHotbar()
```

```lua Example
-- Hotbar anzeigen
exports['jaksam_inventory']:showHotbar()

-- Hotbar nach Erhalt eines Items anzeigen
AddEventHandler('myScript:itemReceived', function()
    exports['jaksam_inventory']:showHotbar()
end)
```

</CodeGroup>

### Parameter

Keine.

### Rückgabewert

Keiner. Zeigt die Hotbar-UI, die sich automatisch nach 2 Sekunden ausblendet.

### Hinweise

- Die Hotbar zeigt die Slots 1-5 aus dem Inventar des Spielers
- Ist `config.dynamicHotbar` auf true gesetzt, werden leere Slots am Ende ausgeblendet
- Die Hotbar blendet sich automatisch nach 2 Sekunden aus
- Mehrfache Aufrufe setzen den Ausblend-Timer zurück
