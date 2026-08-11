---
title: "Get item from slot"
description: "Ruft ein Item aus einem bestimmten Slot im Inventar des Spielers ab."
icon: "grid-2"
---

Ruft ein Item aus einem bestimmten Slot im Inventar des Spielers ab.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemFromSlot(slotId)
```

```lua Example
-- Item aus Slot 5 des Spielers abrufen
local item = exports['jaksam_inventory']:getItemFromSlot(5)

if item then
    print('Item name:', item.name)
    print('Amount:', item.amount)
    if item.metadata then
        print('Metadata:', json.encode(item.metadata))
    end
else
    print('Slot 5 is empty')
end

-- Prüfen, ob ein bestimmter Slot eine Waffe enthält
local slotItem = exports['jaksam_inventory']:getItemFromSlot(1)
if slotItem then
  local staticItem = exports['jaksam_inventory']:getStaticItem(slotItem.name)
  if staticItem and staticItem.type == 'weapon' then
    print('Found weapon in slot 1:', slotItem.name)
  end
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `slotId` | number | Die Slot-Nummer, aus der das Item abgerufen werden soll (im Inventar des Spielers) |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `item` | table \| nil | Das Item im Slot (`name`, `amount`, `metadata`), oder nil falls der Slot leer ist |
