---
title: "Create inventory"
description: "Creates a new inventory in both database and memory (depending on options)."
icon: "square-plus"
---

Creates a new inventory in both database and memory (depending on options). If an inventory with the same ID already exists, returns the existing one without modifying it.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:createInventory(id, label, options, items, inventoryType, metadata)
```

```lua Example
-- Example: Create a loot crate with dynamic loot based on rarity
-- Don't forget to secure the event somehow depending on your use case, otherwise cheaters can simply trigger the event to get free loot
RegisterNetEvent('myresource:openLootCrate', function(rarity)
    local playerId = source

    -- Define loot pools based on rarity
    local lootPools = {
        common = {
            minTypes = 1,
            maxTypes = 2,
            items = {
                { name = "water",   chance = 15, min = 1, max = 3 },
                { name = "bread",   chance = 15, min = 1, max = 2 },
                { name = "bandage", chance = 10, min = 1, max = 2 },
            }
        },
        rare = {
            minTypes = 2,
            maxTypes = 4,
            items = {
                { name = "water",         chance = 10, min = 2, max = 4 },
                { name = "bread",         chance = 8,  min = 2, max = 3 },
                { name = "bandage",       chance = 8,  min = 2, max = 3 },
                { name = "lockpick",      chance = 5,  min = 1, max = 2 },
                { name = "weapon_pistol", chance = 2,  min = 1, max = 1 },
            }
        },
        legendary = {
            minTypes = 3,
            maxTypes = 5,
            items = {
                { name = "water",         chance = 8,  min = 3, max = 5 },
                { name = "bandage",       chance = 8,  min = 3, max = 4 },
                { name = "lockpick",      chance = 6,  min = 2, max = 3 },
                { name = "weapon_pistol", chance = 4,  min = 1, max = 1 },
                { name = "weapon_rifle",  chance = 2,  min = 1, max = 1 },
            }
        }
    }

    local selectedLoot = lootPools[rarity] or lootPools.common

    local inventory = exports['jaksam_inventory']:createInventory(
        nil, -- Auto generate ID
        "Loot Crate (" .. rarity .. ")", -- Dynamic label
        {
            temporary = true, -- Inventory will be lost on script restart
            maxSlots = 5,
            maxWeight = 50.0,
            disableIncoming = true, -- Items cannot be added to this inventory by the player
            prefillItems = selectedLoot,
            revealItems = {
                delayPerItem = 1000,
                randomOrder = true
            }
        },
        nil,
        'stash',
        nil
    )

    -- Open the inventory interface for the player
    if inventory then
        exports['jaksam_inventory']:forceOpenInventory(playerId, inventory.id)
    end
end)
```

```lua Example: persistent stash
-- Create a persistent stash with fixed starting items
local inventory = exports['jaksam_inventory']:createInventory(
    "welcome_kit_" .. charId,
    "Welcome Kit",
    { maxSlots = 5, maxWeight = 20.0 },
    {
        {"bread", 3, nil},
        {"water", 2, nil},
    },
    'stash',
    nil
)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `id` | string \| nil | Unique identifier for the inventory. If nil, a random ID is generated |
| `label` | string \| nil | Display name for the inventory. If nil, a translation based on inventory type will be used |
| `options` | table | Configuration options for the inventory (see Notes below) |
| `items` | table | Static items to add when the inventory is first created. Array format: `{{itemName, amount, metadata}, ...}`. Ignored if the inventory already exists in the database |
| `inventoryType` | string | Type of inventory. Default: "stash". Other values: "player", "trunk", "glovebox" |
| `metadata` | table | Additional metadata for the inventory |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `inventory` | table \| nil | The created (or existing) inventory table, or nil if creation failed. Structure: `{id, label, options, items, type, totalWeight, metadata}` |

### Notes

`options` fields:

- `maxWeight` (number, optional): Maximum weight capacity
- `maxSlots` (number, optional): Maximum number of slots
- `columns` (number, optional): Number of columns for grid display in the UI (e.g. 10 total slots but 2 columns → 2x5 grid)
- `temporary` (boolean, optional): If true, the inventory is not saved to the database and will be lost on script restart
- `prefillItems` (table, optional): Random loot configuration. Items are picked via weighted selection without replacement:
  - `minTypes` (number, optional): Minimum number of different item types to add. Default: 1
  - `maxTypes` (number, optional): Maximum number of different item types to add. Default: pool size
  - `items` (table, required): Array of possible items, each entry: `{name = string, chance = number, min = number, max = number, metadata = table?}`
- `revealItems` (table, optional): Progressive item reveal animation when the inventory is opened:
  - `delayPerItem` (number, optional): Milliseconds between each item reveal. Default: 1000
  - `randomOrder` (boolean, optional): If true, items are revealed in random order instead of slot order. Default: false
- `slots` (table, optional): Per-slot configuration. Key is the slot number, value is a `SlotConfig` table: `label`, `image`, `opacity`, `whitelist`, `blacklist`
- `whitelist` / `blacklist` (table, optional): Inventory-level item filters. Format: `{itemName = true, ...}`
- `allowedJobs` (table, optional): Jobs allowed to access this inventory
- `allowedIdentifiers` (table, optional): Character identifiers allowed to access this inventory
- `disableIncoming` / `disableOutgoing` (boolean, optional): Block transfers in or out by the player
- `dropDisabled` (boolean, optional): If true, items cannot be dropped from this inventory
- `noLimitDrag` (boolean, optional): If true, dragging ignores the amount selection dialog and moves the full stack. Used internally for shops

Also:

- If `id` already exists, the existing inventory is returned as is, static `items` and `prefillItems` are NOT re-applied
- `prefillItems` uses weighted random selection without replacement (each item type can only be picked once)
- `prefillItems` is processed via `options`, while static `items` is a separate parameter, they serve different purposes
- Use `temporary = true` for ephemeral inventories (lootboxes, event rewards) to avoid database bloat
