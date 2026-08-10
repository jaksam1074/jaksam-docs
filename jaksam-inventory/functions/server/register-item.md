---
title: "Register item"
description: "Registers a new item definition at runtime (in-memory only, not saved to file)."
icon: "cube"
---

Registers a new item definition at runtime (in-memory only, not saved to file). Only safe, declarative fields are accepted, everything else is rejected at any depth.

<Note>
  Items registered this way will be lost on resource restart. Use this to let external scripts define their own items without editing `_data/items.lua`.
</Note>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerItem(itemName, itemData)
```

```lua Example: consumable
-- Register a simple consumable item
local success, err = exports['jaksam_inventory']:registerItem('energy_drink', {
    label = 'Energy Drink',
    weight = 0.3,
    stackable = true,
    maxStack = 10,
    description = 'Restores some energy',
    image = 'energy_drink.webp',
    consume = 1,
    status = { hunger = 5, thirst = 15 },
})

if not success then
    print('Failed to register item: ' .. err)
end
```

```lua Example: weapon
-- Register a weapon item
local success, err = exports['jaksam_inventory']:registerItem('WEAPON_YOURWEAPON', {
    label = 'Custom Weapon',
    weight = 2.0,
    stackable = false,
    type = 'weapon',
    ammo = 'ammo_9mm',
    durability = 0.15,
    decay = true,
})
```

```lua Example: container
-- Register a container item
local success, err = exports['jaksam_inventory']:registerItem('custom_bag', {
    label = 'Custom Bag',
    weight = 1.0,
    stackable = false,
    type = 'container',
    inventoryOptions = {
        maxSlots = 5,
        maxWeight = 10.0,
    },
})
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `itemName` | string | Unique item identifier (e.g. `'custom_radio'`). Must not already exist in the item registry |
| `itemData` | table | Item definition table (see Notes below for accepted fields) |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | True if the item was registered successfully |
| `errorMessage` | string \| nil | Error description if registration failed |

### Notes

`itemData` only accepts the following safe fields; any other field is silently stripped:

**Required fields:** `label` (string), `weight` (number, >= 0), `stackable` (boolean)

**Optional fields:** `description`, `image`, `close`, `maxStack`, `rarity`, `type`, `customSymbol`, `ammo`, `durability`, `degrade`, `decay`, `consume`, `isGrenadeType`, `separateWeight`, `universal`, `oxClientEvent`, `oxClientExport`, `oxServerExport`

**Optional table fields** (validated recursively, no functions allowed inside): `metadata`, `status`, `useOptions`, `inventoryOptions`, `throwableOptions`, `dynamicMetadata`

Also:

- Items registered with `registerItem` exist only in memory. They are lost on resource restart. If you need persistent items, use the in-game admin menu or add them to `_data/items.lua`
- Unknown items are cleaned up lazily when each inventory is first loaded, not at startup, your script can safely call `registerItem` at any time before the player's inventory is accessed, typically on resource start
- You can combine `registerItem` with `registerUsableItem` to define both the item and its use behavior from an external script
- If the item name already exists, registration is rejected to prevent overwriting file-defined items
- Table fields (like `metadata`, `useOptions`, etc.) are deep-copied, so changes to the original table after registration have no effect
