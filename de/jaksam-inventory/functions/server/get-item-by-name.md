---
title: "Get item by name"
description: "Ruft das erste in einem Inventar gefundene Item mit diesem Namen ab, mit optionaler Metadaten-Filterung."
icon: "tag"
---

Ruft das erste in einem Inventar gefundene Item mit diesem Namen ab, mit optionaler Metadaten-Filterung.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemByName(inventoryId, itemName, metadata)
```

```lua Example
-- Erstes Brot-Item im Inventar des Spielers abrufen
local playerId = 1
local item, slotId = exports['jaksam_inventory']:getItemByName(playerId, 'bread')

if item then
    print('Found bread in slot:', slotId)
    print('Amount in this slot:', item.amount)
    print('Item metadata:', json.encode(item.metadata))
end

-- Waffe mit bestimmter Seriennummer abrufen
local weapon, weaponSlot = exports['jaksam_inventory']:getItemByName(playerId, 'WEAPON_PISTOL', {
    serial = "ABC123"
})

if weapon then
    print('Found weapon in slot:', weaponSlot)
    print('Weapon ammo:', weapon.metadata.ammo)
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| number | Die zu durchsuchende Inventar-ID. Kann eine Spieler-Server-ID (number) oder Inventar-ID (string) sein |
| `itemName` | string | Der Name des zu suchenden Items |
| `metadata` | table | Metadaten, gegen die bei der Suche abgeglichen wird. Falls angegeben, werden nur Items mit passenden Metadaten zurückgegeben |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `item` | table \| nil | Das erste passende gefundene Item, oder nil falls nicht gefunden |
| `slotId` | number \| nil | Die rohe Slot-ID, in der das Item gefunden wurde (1-basierter Index), nil falls kein Item gefunden wurde |
