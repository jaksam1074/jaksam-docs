---
title: "Clear inventory"
description: "Entfernt alle Items aus einem Inventar, mit optionalem Ausschluss bestimmter Items."
icon: "trash"
---

Entfernt alle Items aus einem Inventar, mit optionalem Ausschluss bestimmter Items.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:clearInventory(inventoryId, excludedItems)
```

```lua Example
local playerId = 14

-- Alle Items aus dem Spieler-Inventar entfernen
local success = exports['jaksam_inventory']:clearInventory(playerId)

-- Inventar leeren, aber bestimmte Items behalten
local success = exports['jaksam_inventory']:clearInventory(playerId, 'phone') -- Telefon behalten

-- Inventar leeren, aber mehrere Items behalten
local success = exports['jaksam_inventory']:clearInventory(1, {'phone', 'id_card', 'driver_license'})

-- Stash-Inventar leeren
local success = exports['jaksam_inventory']:clearInventory('police_stash_1')
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die zu leerende Inventar-ID. Kann eine Spieler-Server-ID oder Inventar-ID sein |
| `excludedItems` | string \| table | Items, die vom Leeren ausgeschlossen werden (im Inventar bleiben). Kann ein einzelner Item-Name (string) oder ein Array von Item-Namen (table) sein. Falls nicht angegeben, werden alle Items entfernt |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls das Inventar erfolgreich geleert wurde, false falls das Inventar nicht existiert oder das Datenbank-Update fehlgeschlagen ist |
