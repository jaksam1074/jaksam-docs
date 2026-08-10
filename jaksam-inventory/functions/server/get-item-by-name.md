---
title: "Get item by name"
description: "Gets the first item found in an inventory by its name, with optional metadata filtering."
icon: "tag"
---

Gets the first item found in an inventory by its name, with optional metadata filtering.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemByName(inventoryId, itemName, metadata)
```

```lua Example
-- Get first bread item in player's inventory
local playerId = 1
local item, slotId = exports['jaksam_inventory']:getItemByName(playerId, 'bread')

if item then
    print('Found bread in slot:', slotId)
    print('Amount in this slot:', item.amount)
    print('Item metadata:', json.encode(item.metadata))
end

-- Get weapon with specific serial number
local weapon, weaponSlot = exports['jaksam_inventory']:getItemByName(playerId, 'WEAPON_PISTOL', {
    serial = "ABC123"
})

if weapon then
    print('Found weapon in slot:', weaponSlot)
    print('Weapon ammo:', weapon.metadata.ammo)
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string \| number | The inventory ID to search in. Can be a player server ID (number) or inventory ID (string) |
| `itemName` | string | The name of the item to search for |
| `metadata` | table | Metadata to match against when searching. If provided, only items with matching metadata will be returned |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `item` | table \| nil | The first item found matching the criteria, or nil if not found |
| `slotId` | number \| nil | The raw slot ID where the item was found (1-based index), nil if item not found |
