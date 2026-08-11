---
title: "Save dirty inventories"
description: "Speichert alle geänderten Inventare in der Datenbank."
icon: "floppy-disk"
---

Speichert alle geänderten Inventare in der Datenbank.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:saveDirtyInventories()
```

```lua Example
-- Alle geänderten Inventare speichern
exports['jaksam_inventory']:saveDirtyInventories()

-- Gute Praxis: vor einem Server-Neustart speichern
AddEventHandler('onResourceStop', function(resourceName)
    if resourceName == GetCurrentResourceName() then
        exports['jaksam_inventory']:saveDirtyInventories()
    end
end)
```

</CodeGroup>

### Parameter

Keine.

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls alle Inventare erfolgreich gespeichert wurden |
