---
title: "Get item from slot"
description: "Ruft ein Item aus einem bestimmten Slot in einem Inventar ab."
icon: "grid-2"
---

Ruft ein Item aus einem bestimmten Slot in einem Inventar ab.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemFromSlot(inventoryId, slotId, returnRaw)
```

```lua Example
-- Item aus Slot 5 des Spielers abrufen
local playerId = 1
local item = exports['jaksam_inventory']:getItemFromSlot(playerId, 5)

if item then
    print('Item name:', item.name)
    print('Amount:', item.amount)
    print('Metadata:', json.encode(item.metadata))

    item.metadata.durability = 50 -- Metadaten aktualisieren
    exports['jaksam_inventory']:setItemMetadataInSlot(playerId, 5, item.metadata) -- Metadaten speichern
end

-- Item aus einem Stash abrufen
local stashItem = exports['jaksam_inventory']:getItemFromSlot('police_stash_1', 3)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die Inventar-ID, aus der das Item abgerufen werden soll. Kann eine Spieler-Server-ID (number) oder Inventar-ID (string) sein |
| `slotId` | number | Die Slot-Nummer, aus der das Item abgerufen werden soll |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `item` | table \| nil | Das Item im Slot (`name`, `amount`, `metadata`), oder nil falls der Slot leer ist |

### Hinweise

<Info>
  [TODO: INFORMATION NEEDED] Die Export-Signatur akzeptiert einen dritten Parameter `returnRaw`, der im Quellmaterial für diese Seite nicht dokumentiert ist.
</Info>
