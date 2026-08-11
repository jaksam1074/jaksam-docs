---
title: "Set item metadata in slot"
description: "Aktualisiert die Metadaten eines Items in einem bestimmten Inventar-Slot."
icon: "grid-2"
---

Aktualisiert die Metadaten eines Items in einem bestimmten Inventar-Slot.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setItemMetadataInSlot(inventoryId, slotId, metadata)
```

```lua Example
-- Waffenmunition aktualisieren
exports['jaksam_inventory']:setItemMetadataInSlot(1, 5, {
    serial = "ABC123",
    ammo = 6 -- Munitionsanzahl aktualisieren
})

-- Item-Haltbarkeit aktualisieren
exports['jaksam_inventory']:setItemMetadataInSlot(1, 3, {
    durability = 50
})
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die Inventar-ID, die das Item enthält |
| `slotId` | number | Der Slot, der das zu aktualisierende Item enthält |
| `metadata` | table | Die zu setzenden neuen Metadaten |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls die Metadaten erfolgreich aktualisiert wurden |
| `resultCode` | string | Fehlermeldung, falls der Vorgang fehlgeschlagen ist |
