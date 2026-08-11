---
title: "Open inventory"
description: "Öffnet ein Inventar neben dem Inventar des Spielers."
icon: "door-open"
---

Öffnet ein Inventar neben dem Inventar des Spielers.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:openInventory(inventoryId)
```

```lua Example
-- Ein Stash-Inventar öffnen
exports['jaksam_inventory']:openInventory('police_stash_1')

-- Ein Kofferraum-Inventar öffnen
exports['jaksam_inventory']:openInventory('car_trunk_123')
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string | Die ID des zu öffnenden Inventars |

### Rückgabewert

Keiner. Öffnet bei Erfolg die Inventar-UI.
