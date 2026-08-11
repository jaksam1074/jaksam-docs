---
title: "Close inventory"
description: "Schließt die Inventar-UI. Kann entweder ein bestimmtes Inventar oder die gesamte Inventar-UI schließen."
icon: "door-closed"
---

Schließt die Inventar-UI. Kann entweder ein bestimmtes Inventar oder die gesamte Inventar-UI schließen.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:closeInventory(inventoryId)
```

```lua Example
-- Die gesamte Inventar-UI schließen
exports['jaksam_inventory']:closeInventory()

-- Ein bestimmtes Inventar schließen (z.B. einen Stash)
exports['jaksam_inventory']:closeInventory('police_stash_1')

-- Inventar nach einem bestimmten Event erzwungen schließen
AddEventHandler('myScript:forceCloseInventory', function()
    exports['jaksam_inventory']:closeInventory()
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| nil | Falls angegeben, wird nur das angegebene Inventar aus der UI entfernt. Bei nil wird die gesamte Inventar-UI und alle offenen Inventare geschlossen |

### Rückgabewert

Keiner.
