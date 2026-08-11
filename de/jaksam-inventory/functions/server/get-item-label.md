---
title: "Get item label"
description: "Ruft das Anzeige-Label eines Items ab."
icon: "tag"
---

Ruft das Anzeige-Label eines Items ab.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemLabel(itemName)
```

```lua Example
-- Item-Label abrufen
local label = exports['jaksam_inventory']:getItemLabel('bread')
print(label) -- gibt "Bread" oder das jeweils gesetzte Label aus

-- Prüfen, ob ein Item über sein Label existiert (funktioniert zwar, aber getStaticItem ist der bessere Weg)
if not exports['jaksam_inventory']:getItemLabel('invalid_item') then
    print('Item does not exist')
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `itemName` | string | Der Name des Items, dessen Label abgerufen werden soll |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `label` | string \| nil | Das Anzeige-Label des Items, nil falls das Item nicht existiert |
