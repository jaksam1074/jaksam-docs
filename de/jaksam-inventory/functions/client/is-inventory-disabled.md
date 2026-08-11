---
title: "Is inventory disabled"
description: "Gibt zurück, ob das Öffnen des Inventars aktuell deaktiviert ist."
icon: "ban"
---

Gibt zurück, ob das Öffnen des Inventars aktuell deaktiviert ist.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:isInventoryDisabled()
```

```lua Example
-- Vor einer Aktion prüfen, ob das Inventar deaktiviert ist
local disabled = exports['jaksam_inventory']:isInventoryDisabled()

if disabled then
    print('Inventory is currently disabled')
end

-- Eine eigene Aktion absichern
if not exports['jaksam_inventory']:isInventoryDisabled() then
    exports['jaksam_inventory']:openInventory('my_stash')
end
```

</CodeGroup>

### Parameter

Keine.

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `disabled` | boolean | True, falls das Öffnen des Inventars aktuell deaktiviert ist, sonst false |
