---
title: "Get total item amount"
description: "Gibt die Gesamtmenge eines bestimmten Items in einem Inventar zurück, inklusive Items in Behältern."
icon: "hashtag"
---

Gibt die Gesamtmenge eines bestimmten Items in einem Inventar zurück, inklusive Items in Behältern.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getTotalItemAmount(inventoryId, itemName, metadata, skipContainers)
```

```lua Example
-- Gesamtmenge Brot im Inventar abrufen
local total = exports['jaksam_inventory']:getTotalItemAmount(1, 'bread')

-- Menge mit bestimmten Metadaten abrufen
local total = exports['jaksam_inventory']:getTotalItemAmount(1, 'weapon_pistol', {
    serial = "ABC123"
})

-- Menge ohne Behälter abrufen
local total, totalNoContainers = exports['jaksam_inventory']:getTotalItemAmount(1, 'bread', nil, true)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die zu prüfende Inventar-ID |
| `itemName` | string | Der Name des zu zählenden Items |
| `metadata` | table | Metadaten, gegen die beim Zählen abgeglichen werden (falls angegeben, werden nur Items mit gleicher Metadata UND gleichem Namen gezählt) |
| `skipContainers` | boolean | Bei true werden Items in Behältern nicht mitgezählt |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `totalAmount` | number | Gesamtmenge des Items im Inventar, inklusive Behälter (nur falls skipContainers false ist) |
| `totalAmountContainersExcluded` | number \| nil | Gesamtmenge ohne Behälter (nur falls skipContainers false ist) |
