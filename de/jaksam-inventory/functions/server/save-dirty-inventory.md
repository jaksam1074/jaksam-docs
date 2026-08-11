---
title: "Save dirty inventory"
description: "Speichert ein bestimmtes Inventar in der Datenbank, falls es geändert wurde."
icon: "floppy-disk"
---

Speichert ein bestimmtes Inventar in der Datenbank, falls es geändert wurde.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:saveDirtyInventory(inventoryId)
```

```lua Example
-- Bestimmtes Inventar speichern
exports['jaksam_inventory']:saveDirtyInventory('police_stash_1')

-- Spieler-Inventar nach wichtigen Änderungen speichern
local success = exports['jaksam_inventory']:saveDirtyInventory(1)
if not success then
    print('Failed to save inventory')
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die ID des zu speichernden Inventars |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls das Inventar erfolgreich gespeichert wurde |
