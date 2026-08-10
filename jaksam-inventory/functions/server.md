---
title: "Server"
icon: "server"
description: "Full reference of server-side exports for managing inventories, items, stashes, and vehicles"
---

## Compatibility

This script works with other popular inventory systems, like es_extended, qb-inventory, and ox_inventory.

<Info>
  For ESX and QBCore functions, the setup is done automatically. But, if you want to keep using exports from ox_inventory or qb-inventory for compatibility, you need to turn on this option in the file: `jaksam_inventory/integrations/sv_integrations.lua`
</Info>

## Server functions

Here there are built-in exports of jaksam's inventory.

## addItem

Adds items to an inventory with support for metadata and specific slot placement.

```lua
exports['jaksam_inventory']:addItem(inventoryId, itemName, amount, metadata, slotId)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to add items to. Can be a player server ID or inventory ID
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to add
</ParamField>

<ParamField path="amount" type="number" required>
  How many items to add
</ParamField>

<ParamField path="metadata" type="table">
  Additional data for the item (e.g. weapon serial, item durability)
</ParamField>

<ParamField path="slotId" type="number">
  Specific slot to place the item in
</ParamField>

**Returns:**

- `success` (boolean) — true if items were added successfully
- `resultCode` (string) — Error message if the operation failed

```lua
-- Add 5 bread to a player's inventory
local success, result = exports['jaksam_inventory']:addItem(1, 'bread', 5)

-- Add a weapon with metadata
local success, result = exports['jaksam_inventory']:addItem(1, 'WEAPON_PISTOL', 1, {
    serial = "ABC123",
    ammo = 12
})

-- Add item to specific slot
local success, result = exports['jaksam_inventory']:addItem(1, 'bread', 1, nil, 5) -- slot 5
```

## addItemToTrunk

Adds items to a vehicle trunk using only the vehicle plate, automatically resolving the full inventory ID.

```lua
exports['jaksam_inventory']:addItemToTrunk(plate, itemName, amount, metadata, slotId)
```

<ParamField path="plate" type="string" required>
  The vehicle license plate
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to add
</ParamField>

<ParamField path="amount" type="number" required>
  How many items to add
</ParamField>

<ParamField path="metadata" type="table">
  Additional data for the item
</ParamField>

<ParamField path="slotId" type="number">
  Specific slot to place the item in
</ParamField>

**Returns:**

- `success` (boolean) — true if items were added successfully
- `resultCode` (string) — Error message if the operation failed (e.g., "vehicle_not_found")
- `notificationType` (string) — Type of notification to show to the user

```lua
-- Add 5 water bottles to vehicle trunk
local plate = GetVehicleNumberPlateText(vehicle)
local success, result = exports['jaksam_inventory']:addItemToTrunk(plate, 'water', 5)

if not success then
    print("Failed to add item: " .. result)
end

-- Add item with metadata
local success = exports['jaksam_inventory']:addItemToTrunk("ABC 123", 'phone', 1, {
    number = "555-0123"
})
```

<Note>
  - Works with owned vehicles (even if not spawned/in garage)
  - Works with NPC vehicles (if currently spawned)
  - Automatically creates trunk inventory if it doesn't exist
  - For owned vehicles, inventory is persistent (saved to database)
</Note>

## addItemToGlovebox

Adds items to a vehicle glovebox using only the vehicle plate, automatically resolving the full inventory ID.

```lua
exports['jaksam_inventory']:addItemToGlovebox(plate, itemName, amount, metadata, slotId)
```

<ParamField path="plate" type="string" required>
  The vehicle license plate
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to add
</ParamField>

<ParamField path="amount" type="number" required>
  How many items to add
</ParamField>

<ParamField path="metadata" type="table">
  Additional data for the item
</ParamField>

<ParamField path="slotId" type="number">
  Specific slot to place the item in
</ParamField>

**Returns:**

- `success` (boolean) — true if items were added successfully
- `resultCode` (string) — Error message if the operation failed (e.g., "vehicle_not_found")
- `notificationType` (string) — Type of notification to show to the user

```lua
-- Add documents to glovebox
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:addItemToGlovebox(plate, 'documents', 1)

-- Add multiple items
local success = exports['jaksam_inventory']:addItemToGlovebox("XYZ 789", 'money', 500)
```

<Note>
  - Works with owned vehicles (even if not spawned/in garage)
  - Works with NPC vehicles (if currently spawned)
  - Automatically creates glovebox inventory if it doesn't exist
  - For owned vehicles, inventory is persistent (saved to database)
</Note>

## removeItemFromTrunk

Removes items from a vehicle trunk using only the vehicle plate, automatically resolving the full inventory ID.

```lua
exports['jaksam_inventory']:removeItemFromTrunk(plate, itemName, amount, metadata, slotId)
```

<ParamField path="plate" type="string" required>
  The vehicle license plate
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to remove
</ParamField>

<ParamField path="amount" type="number" required>
  How many items to remove
</ParamField>

<ParamField path="metadata" type="table">
  Metadata to match for removal (optional filtering)
</ParamField>

<ParamField path="slotId" type="number">
  Specific slot to remove from
</ParamField>

**Returns:**

- `success` (boolean) — true if items were removed successfully
- `resultCode` (string) — Error message if the operation failed
- `notificationType` (string) — Type of notification to show to the user

```lua
-- Remove 3 water bottles from trunk
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:removeItemFromTrunk(plate, 'water', 3)

-- Remove from specific slot
local success = exports['jaksam_inventory']:removeItemFromTrunk("ABC 123", 'weapon', 1, nil, 5)
```

<Note>
  Vehicle must exist (owned vehicle in database or NPC vehicle currently spawned). Returns false with "vehicle_not_found" if vehicle doesn't exist.
</Note>

## removeItemFromGlovebox

Removes items from a vehicle glovebox using only the vehicle plate, automatically resolving the full inventory ID.

```lua
exports['jaksam_inventory']:removeItemFromGlovebox(plate, itemName, amount, metadata, slotId)
```

<ParamField path="plate" type="string" required>
  The vehicle license plate
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to remove
</ParamField>

<ParamField path="amount" type="number" required>
  How many items to remove
</ParamField>

<ParamField path="metadata" type="table">
  Metadata to match for removal (optional filtering)
</ParamField>

<ParamField path="slotId" type="number">
  Specific slot to remove from
</ParamField>

**Returns:**

- `success` (boolean) — true if items were removed successfully
- `resultCode` (string) — Error message if the operation failed
- `notificationType` (string) — Type of notification to show to the user

```lua
-- Remove documents from glovebox
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:removeItemFromGlovebox(plate, 'documents', 1)

if not success then
    print("Document not found in glovebox")
end
```

<Note>
  Vehicle must exist (owned vehicle in database or NPC vehicle currently spawned). Returns false with "vehicle_not_found" if vehicle doesn't exist.
</Note>

## getInventoryIdFromPlate

Resolves the full inventory ID for a vehicle compartment using only the vehicle plate.

```lua
exports['jaksam_inventory']:getInventoryIdFromPlate(plate, compartment)
```

<ParamField path="plate" type="string" required>
  The vehicle license plate
</ParamField>

<ParamField path="compartment" type="string" required>
  Either "trunk" or "glovebox"
</ParamField>

**Returns:** `inventoryId` (string | nil) — The full inventory ID (format: `"vehicle:plate:model:compartment"`), nil if vehicle not found

```lua
-- Get trunk inventory ID
local plate = GetVehicleNumberPlateText(vehicle)
local trunkId = exports['jaksam_inventory']:getInventoryIdFromPlate(plate, "trunk")

if trunkId then
    print("Trunk ID: " .. trunkId)
    -- Now you can use standard inventory functions
    local inventory = exports['jaksam_inventory']:getInventory(trunkId)
end

-- Get glovebox inventory ID
local gloveboxId = exports['jaksam_inventory']:getInventoryIdFromPlate("ABC 123", "glovebox")
```

<Note>
  Searches in this order:

  1. Owned vehicles database (ESX: `owned_vehicles`, QBCore: `player_vehicles`)
  2. Existing inventories in `jaksam_inventory` table
  3. Currently spawned vehicles (GetAllVehicles - NPC vehicles)

  For owned vehicles, automatically creates inventory if it doesn't exist. Created inventories are persistent for owned vehicles, temporary for NPC vehicles. Works even if vehicle is not currently spawned (garage).
</Note>

## canCarryItem

Checks if an inventory has space for additional items, considering both weight and slot limits.

```lua
exports['jaksam_inventory']:canCarryItem(inventoryId, itemName, amount)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to check. Can be a player server ID or inventory ID
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to check
</ParamField>

<ParamField path="amount" type="number" required>
  How many items to check for
</ParamField>

**Returns:** `boolean` — true if the inventory can carry the items, false if adding would exceed weight or slot limits

```lua
-- Check if player can carry 5 bread
local canCarry = exports['jaksam_inventory']:canCarryItem(1, 'bread', 5)

if canCarry then
    -- Safe to add items
    exports['jaksam_inventory']:addItem(1, 'bread', 5)
end
```

## canSwapItem

Checks if swapping firstItem (removing firstItemCount) with testItem (adding testItemCount) is possible.

```lua
exports['jaksam_inventory']:canSwapItem(inventoryId, firstItem, firstItemCount, testItem, testItemCount)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to check. Can be a player server ID or inventory ID
</ParamField>

<ParamField path="firstItem" type="string" required>
  The name of the item to check
</ParamField>

<ParamField path="firstItemCount" type="number" required>
  How many items to remove
</ParamField>

<ParamField path="testItem" type="string" required>
  The name of the item to add
</ParamField>

<ParamField path="testItemCount" type="number" required>
  How many items to add
</ParamField>

**Returns:** `boolean` — true if the inventory can swap the items, false if swapping is not possible

```lua
-- Check if player can swap 5 bread for 1 water
local playerId = 1
local canSwap = exports['jaksam_inventory']:canSwapItem(playerId, 'bread', 5, 'water', 1)

if canSwap then
    exports['jaksam_inventory']:removeItem(playerId, 'bread', 5)
    exports['jaksam_inventory']:addItem(playerId, 'water', 1)
end
```

## clearInventory

Removes all items from an inventory, with optional exclusion of specific items.

```lua
exports['jaksam_inventory']:clearInventory(inventoryId, excludedItems)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to clear. Can be a player server ID or inventory ID
</ParamField>

<ParamField path="excludedItems" type="string | table">
  Items to exclude from clearing (keep in inventory). Can be a single item name (string) or an array of item names (table). If not provided, all items will be removed
</ParamField>

**Returns:** `success` (boolean) — true if inventory was cleared successfully, false if inventory doesn't exist or database update failed

```lua
local playerId = 14

-- Clear all items from player inventory
local success = exports['jaksam_inventory']:clearInventory(playerId)

-- Clear inventory but keep specific items
local success = exports['jaksam_inventory']:clearInventory(playerId, 'phone') -- keep phone

-- Clear inventory but keep multiple items
local success = exports['jaksam_inventory']:clearInventory(1, {'phone', 'id_card', 'driver_license'})

-- Clear stash inventory
local success = exports['jaksam_inventory']:clearInventory('police_stash_1')
```

## createInventory

Creates a new inventory in both database and memory (depending on options). If an inventory with the same ID already exists, returns the existing one without modifying it.

```lua
exports['jaksam_inventory']:createInventory(id, label, options, items, inventoryType, metadata)
```

<ParamField path="id" type="string | nil">
  Unique identifier for the inventory. If nil, a random ID is generated
</ParamField>

<ParamField path="label" type="string | nil">
  Display name for the inventory. If nil, a translation based on inventory type will be used
</ParamField>

<ParamField path="options" type="table">
  Configuration options for the inventory:

  - `maxWeight` (number, optional): Maximum weight capacity
  - `maxSlots` (number, optional): Maximum number of slots
  - `columns` (number, optional): Number of columns for grid display in the UI (e.g. 10 total slots but 2 columns → 2x5 grid)
  - `temporary` (boolean, optional): If true, the inventory is not saved to the database and will be lost on script restart
  - `prefillItems` (table, optional): Random loot configuration. Items are picked via weighted selection without replacement:
    - `minTypes` (number, optional): Minimum number of different item types to add. Default: 1
    - `maxTypes` (number, optional): Maximum number of different item types to add. Default: pool size
    - `items` (table, **required**): Array of possible items, each entry: `{name = string, chance = number, min = number, max = number, metadata = table?}`
  - `revealItems` (table, optional): Progressive item reveal animation when the inventory is opened:
    - `delayPerItem` (number, optional): Milliseconds between each item reveal. Default: 1000
    - `randomOrder` (boolean, optional): If true, items are revealed in random order instead of slot order. Default: false
  - `slots` (table, optional): Per-slot configuration. Key is the slot number, value is a `SlotConfig` table:
    - `label`, `image`, `opacity`, `whitelist`, `blacklist`
  - `whitelist` / `blacklist` (table, optional): Inventory-level item filters. Format: `{itemName = true, ...}`
  - `allowedJobs` (table, optional): Jobs allowed to access this inventory
  - `allowedIdentifiers` (table, optional): Character identifiers allowed to access this inventory
  - `disableIncoming` / `disableOutgoing` (boolean, optional): Block transfers in or out by the player
  - `dropDisabled` (boolean, optional): If true, items cannot be dropped from this inventory
  - `noLimitDrag` (boolean, optional): If true, dragging ignores the amount selection dialog and moves the full stack. Used internally for shops
</ParamField>

<ParamField path="items" type="table">
  Static items to add when the inventory is first created. Array format: `{{itemName, amount, metadata}, ...}`. Ignored if the inventory already exists in the database
</ParamField>

<ParamField path="inventoryType" type="string">
  Type of inventory. Default: "stash". Other values: "player", "trunk", "glovebox"
</ParamField>

<ParamField path="metadata" type="table">
  Additional metadata for the inventory
</ParamField>

**Returns:** `inventory` (Inventory | nil) — The created (or existing) inventory table, or nil if creation failed. Structure: `{id, label, options, items, type, totalWeight, metadata}`

```lua
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

```lua
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

<Note>
  - If `id` already exists, the existing inventory is returned as is, static `items` and `prefillItems` are NOT re-applied
  - `prefillItems` uses weighted random selection **without replacement** (each item type can only be picked once)
  - `prefillItems` is processed via `options`, while static `items` is a separate parameter — they serve different purposes
  - Use `temporary = true` for ephemeral inventories (lootboxes, event rewards) to avoid database bloat
</Note>

## forceOpenInventory

Forces an inventory to be opened for a specific player without permission checks.

```lua
exports['jaksam_inventory']:forceOpenInventory(playerId, inventoryId)
```

<ParamField path="playerId" type="number" required>
  The server ID of the player who will see the inventory
</ParamField>

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to open. Can be a player server ID (number) or inventory ID (string)
</ParamField>

**Returns:** This function doesn't return any value

```lua
-- Open a stash for a player
local playerId = 1
exports['jaksam_inventory']:forceOpenInventory(playerId, 'police_stash_1')

-- Open another player's inventory (search/rob)
local targetPlayerId = 2
exports['jaksam_inventory']:forceOpenInventory(playerId, targetPlayerId)

-- Open inventory from a custom menu/UI
RegisterNetEvent('myresource:openCustomStorage', function(storageId)
    local playerId = source
    exports['jaksam_inventory']:forceOpenInventory(playerId, storageId)
end)
```

## getInventory

Gets complete data about an inventory including its items, weight limits, and metadata.

```lua
exports['jaksam_inventory']:getInventory(inventoryId)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to get data for. Can be a player server ID (number) or inventory ID (string)
</ParamField>

**Returns:** `inventory` (table | nil)

```lua
{
    id = string,          -- Unique identifier of the inventory
    label = string,       -- Display name of the inventory
    type = string,        -- Type of inventory (e.g. "player", "stash", "trunk")
    options = table,      -- Inventory options and settings
    items = table,        -- Items contained in the inventory
    totalWeight = number, -- Current total weight of inventory
    limits = {
        maxSlots = number,  -- Maximum number of slots
        maxWeight = number  -- Maximum weight capacity
    },
    metadata = table      -- Additional inventory metadata
}
```

```lua
-- Get a player's inventory
local inventory = exports['jaksam_inventory']:getInventory(1) -- player with server ID 1

-- Get a stash inventory
local stashInv = exports['jaksam_inventory']:getInventory('police_stash_1')

if inventory then
    print(inventory.totalWeight) -- prints current weight
    print(inventory.limits.maxWeight) -- prints max weight allowed
    print(json.encode(inventory.items, {indent = true})) -- {["SLOT-4"] = {name = "itemName", amount = 1, metadata = {}}}
end
```

## getItemFromSlot

Gets an item from a specific slot in an inventory.

```lua
exports['jaksam_inventory']:getItemFromSlot(inventoryId, slotId, returnRaw)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to get the item from. Can be a player server ID (number) or inventory ID (string)
</ParamField>

<ParamField path="slotId" type="number" required>
  The slot number to get the item from
</ParamField>

**Returns:** `item` (table | nil) — The item in the slot, or nil if the slot is empty

```lua
{
    name = string,     -- Item name
    amount = number,   -- Item amount
    metadata = table   -- Item metadata
}
```

```lua
-- Get item from player's slot 5
local playerId = 1
local item = exports['jaksam_inventory']:getItemFromSlot(playerId, 5)

if item then
    print('Item name:', item.name)
    print('Amount:', item.amount)
    print('Metadata:', json.encode(item.metadata))

    item.metadata.durability = 50 -- update metadata
    exports['jaksam_inventory']:setItemMetadataInSlot(playerId, 5, item.metadata) -- save metadata
end

-- Get item from stash
local stashItem = exports['jaksam_inventory']:getItemFromSlot('police_stash_1', 3)
```

## getItemByName

Gets the first item found in an inventory by its name, with optional metadata filtering.

```lua
exports['jaksam_inventory']:getItemByName(inventoryId, itemName, metadata)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to search in. Can be a player server ID (number) or inventory ID (string)
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to search for
</ParamField>

<ParamField path="metadata" type="table">
  Metadata to match against when searching. If provided, only items with matching metadata will be returned
</ParamField>

**Returns:**

- `item` (table | nil) — The first item found matching the criteria, or nil if not found
- `slotId` (number | nil) — The raw slot ID where the item was found (1-based index), nil if item not found

```lua
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

## getItemsByName

Gets all items from an inventory by name, with optional metadata filtering.

```lua
exports['jaksam_inventory']:getItemsByName(inventoryId, itemName, metadata, strict)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to search in. Can be a player server ID (number) or inventory ID (string)
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the items to search for
</ParamField>

<ParamField path="metadata" type="table">
  Metadata to match against when searching. If provided, only items with matching metadata will be returned
</ParamField>

<ParamField path="strict" type="boolean">
  Whether to match the metadata strictly (default: nil). If true, all metadata fields must match exactly
</ParamField>

**Returns:** `items` (table) — Array of all items found matching the criteria. Empty table `{}` if no items found

```lua
{
    name = string,     -- Item name
    amount = number,   -- Item amount in that specific slot
    metadata = table,  -- Item metadata or nil
    slot = number      -- Raw slot ID where the item was found (1-based index)
}
```

```lua
-- Get all bread items in player's inventory
local playerId = 1
local breads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')

print('Found ' .. #breads .. ' bread stacks')
for i = 1, #breads do
    local bread = breads[i]
    print('Slot ' .. bread.slot .. ': ' .. bread.amount .. ' breads')
end

-- Get all weapons with specific metadata (ammo = 0)
local weapons = exports['jaksam_inventory']:getItemsByName(playerId, 'WEAPON_PISTOL', {
    ammo = 0
})

-- Calculate total amount across all slots (getTotalItemAmount is suggested to use instead)
local totalBread = 0
local allBreads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')
for i = 1, #allBreads do
    totalBread = totalBread + allBreads[i].amount
end
print('Total bread amount:', totalBread)

-- Remove all bread from inventory
local breads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')
for i = 1, #breads do
    exports['jaksam_inventory']:removeItem(playerId, 'bread', breads[i].amount, nil, breads[i].slot)
end
```

<Note>
  - Each item includes the `slot` field indicating where it was found
  - Use this when you need to process multiple stacks of the same item
  - For single item lookups, prefer `getItemByName` for better performance
</Note>

## getItemLabel

Gets the display label of an item.

```lua
exports['jaksam_inventory']:getItemLabel(itemName)
```

<ParamField path="itemName" type="string" required>
  The name of the item to get the label for
</ParamField>

**Returns:** `label` (string | nil) — The display label of the item, nil if item doesn't exist

```lua
-- Get item label
local label = exports['jaksam_inventory']:getItemLabel('bread')
print(label) -- prints "Bread" or whatever label is set

-- Check if item exists using label (despite this would work, the best way would be to use getStaticItem)
if not exports['jaksam_inventory']:getItemLabel('invalid_item') then
    print('Item does not exist')
end
```

## getTotalItemAmount

Returns the total amount of a specific item in an inventory, including items in containers.

```lua
exports['jaksam_inventory']:getTotalItemAmount(inventoryId, itemName, metadata, skipContainers)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to check
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to count
</ParamField>

<ParamField path="metadata" type="table">
  Metadata to match against when counting (if provided, only items with the same metadata AND name will be counted)
</ParamField>

<ParamField path="skipContainers" type="boolean">
  If true, items in containers will not be counted
</ParamField>

**Returns:**

- `totalAmount` (number) — Total amount of the item in the inventory, including containers (only if skipContainers is false)
- `totalAmountContainersExcluded` (number | nil) — Total amount excluding containers (only if skipContainers is false)

```lua
-- Get total amount of bread in inventory
local total = exports['jaksam_inventory']:getTotalItemAmount(1, 'bread')

-- Get amount with specific metadata
local total = exports['jaksam_inventory']:getTotalItemAmount(1, 'weapon_pistol', {
    serial = "ABC123"
})

-- Get amount excluding containers
local total, totalNoContainers = exports['jaksam_inventory']:getTotalItemAmount(1, 'bread', nil, true)
```

## hasItem

Checks if an inventory has a specific item.

```lua
exports['jaksam_inventory']:hasItem(inventoryId, itemName, quantity)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to check
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to check
</ParamField>

<ParamField path="quantity" type="number">
  How many items to check for. Default is 1
</ParamField>

**Returns:** `boolean` — true if the inventory has the item, false if not

```lua
-- Check if player has 5 bread
local hasItem = exports['jaksam_inventory']:hasItem(1, 'bread', 5)

if hasItem then
    -- Safe to remove items
    exports['jaksam_inventory']:removeItem(1, 'bread', 5)
end
```

## registerUsableItem

Registers a callback function that will be called when an item is used. Framework specific registering item will work anyway, as `ESX.RegisterUsableItem` and QBCore's equivalent.

```lua
exports['jaksam_inventory']:registerUsableItem(itemName, callback)
```

<ParamField path="itemName" type="string" required>
  The name of the item to register
</ParamField>

<ParamField path="callback" type="function" required>
  Function to call when item is used. Parameters on ESX: `playerId, itemName, inventoryItem` (`name`, `metadata`, `amount`). Parameters on QBCore: `playerId, inventoryItem` (`name`, `metadata`, `amount`, etc.)
</ParamField>

**Returns:** `success` (boolean) — true if registration was successful

```lua
-- Register usable item on ESX
exports['jaksam_inventory']:registerUsableItem('bread', function(playerId, itemName, inventoryItem)
    -- Heal player when bread is used
    local plyPed = GetPlayerPed(playerId)
    local health = GetEntityHealth(plyPed)
    SetEntityHealth(plyPed, math.min(health + 20, 200))
end)

-- Register usable item on ESX showing used item metadata
exports['jaksam_inventory']:registerUsableItem('armour', function(playerId, itemName, inventoryItem)
    print("Armor has still " .. inventoryItem.metadata.value .. "% of durability")
end)
```

```lua
-- Register usable item on QBCore
exports['jaksam_inventory']:registerUsableItem('armour', function(playerId, item)
    print("Armor has still " .. item.metadata.value .. "% of durability")
end)
```

## registerStash

Dynamically registers a new stash and creates its server inventory during runtime.

```lua
exports['jaksam_inventory']:registerStash(options)
```

<ParamField path="options" type="table" required>
  Configuration table for the stash:

  - `id` (string, optional): Unique ID for the stash. If not provided, one will be autogenerated
  - `label` (string, **required**): Display name for the stash
  - `coords` (vector3 | table, optional): Location where the stash can be accessed via interaction point
  - `maxWeight` (number, optional): Maximum weight capacity. Default: 100
  - `maxSlots` (number, optional): Maximum number of slots. Default: 100
  - `radius` (number, optional): Distance from which players can access the stash. Default: 3.0
  - `isPrivate` (boolean, optional): If true, creates a separate inventory for each player. Default: false
  - `allowedJobs` (table, optional): Table of job names that can access the stash. If nil, stash is public
  - `temporary` (boolean, optional): If true, stash won't be saved to database and lost on script restart. Default: false
  - `startingItems` (table, optional): Items to add when the stash is first created. Format: `{{itemName, amount, metadata}, ...}`
  - `runtimeOnly` (boolean, optional): If true (default), stash can only be opened programmatically. If false and coords are provided, creates client-side interaction points. Default: true
</ParamField>

**Returns:** `stashId` (string | nil) — The ID of the created stash, nil if creation failed

```lua
-- Create a public stash with interaction point (runtimeOnly = false)
local stashId = exports['jaksam_inventory']:registerStash({
    label = "Public Storage",
    coords = vector3(100.0, 200.0, 30.0),
    maxWeight = 500,
    maxSlots = 50,
    radius = 5.0,
    runtimeOnly = false -- Enable interaction points
})

-- Create a job-restricted stash with interaction point
local policeStashId = exports['jaksam_inventory']:registerStash({
    id = "police_evidence",
    label = "Police Evidence Locker",
    coords = vector3(450.0, -990.0, 30.0),
    maxWeight = 1000,
    maxSlots = 100,
    radius = 3.0,
    allowedJobs = {police = true, sheriff = true},
    runtimeOnly = false -- Enable interaction points
})

-- Create a programmatic-only stash (default behavior, runtimeOnly = true)
-- Players can't access it via world interaction, only through code
local hiddenStashId = exports['jaksam_inventory']:registerStash({
    id = "secret_stash",
    label = "Secret Storage",
    maxWeight = 200,
    maxSlots = 30
    -- No coords provided, accessed only programmatically
})

-- Create a private stash (each player gets their own inventory when accessing the stash)
local privateStashId = exports['jaksam_inventory']:registerStash({
    id = "luxury_apartment_stash",
    label = "Personal Safe",
    coords = vector3(300.0, 400.0, 50.0),
    maxWeight = 200,
    maxSlots = 30,
    isPrivate = true
})

-- Create a temporary stash with starting items (won't save to database)
local tempStashId = exports['jaksam_inventory']:registerStash({
    label = "Event Loot Box",
    coords = vector3(500.0, 600.0, 20.0),
    maxWeight = 100,
    maxSlots = 20,
    temporary = true,
    startingItems = {
        {"bread", 5, nil},
        {"water", 3, nil},
        {"money", 1000, nil}
    }
})

-- Create a menu-based stash (runtimeOnly = true by default)
-- Useful for custom UI/menu systems
local virtualStashId = exports['jaksam_inventory']:registerStash({
    id = "player_bank_vault",
    label = "Bank Vault",
    maxWeight = 500,
    maxSlots = 50,
    isPrivate = true
    -- runtimeOnly = true by default, accessed only programmatically
})

-- Open stash programmatically from server (e.g., from a menu or command)
RegisterCommand('openvault', function(source)
    local charId = Framework.getPlayerCharIdentifier(source)
    local stashId = "player_bank_vault_" .. charId
    exports['jaksam_inventory']:forceOpenInventory(source, stashId)
end)

-- Alternative: Open from client-side script
-- exports['jaksam_inventory']:openInventory('stashId')
```

## registerItem

Registers a new item definition at runtime (in-memory only, not saved to file). Only safe, declarative fields are accepted — everything else is rejected at any depth.

<Note>
  Items registered this way will be lost on resource restart. Use this to let external scripts define their own items without editing `_data/items.lua`.
</Note>

```lua
exports['jaksam_inventory']:registerItem(itemName, itemData)
```

<ParamField path="itemName" type="string" required>
  Unique item identifier (e.g. `'custom_radio'`). Must not already exist in the item registry
</ParamField>

<ParamField path="itemData" type="table" required>
  Item definition table. Only the following safe fields are accepted; any other field is silently stripped:

  **Required fields:**

  - `label` (string): Display name
  - `weight` (number): Item weight (\>= 0)
  - `stackable` (boolean): Whether the item can stack

  **Optional fields:**

  - `description`, `image`, `close`, `maxStack`, `rarity`, `type`, `customSymbol`, `ammo`, `durability`, `degrade`, `decay`, `consume`, `isGrenadeType`, `separateWeight`, `universal`, `oxClientEvent`, `oxClientExport`, `oxServerExport`

  **Optional table fields** (validated recursively — no functions allowed inside):

  - `metadata`, `status`, `useOptions`, `inventoryOptions`, `throwableOptions`, `dynamicMetadata`
</ParamField>

**Returns:**

- `success` (boolean) — true if the item was registered successfully
- `errorMessage` (string | nil) — Error description if registration failed

```lua
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

```lua
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

```lua
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

<Note>
  - Items registered with `registerItem` exist **only in memory**. They are lost on resource restart. If you need persistent items, use the in-game admin menu or add them to `_data/items.lua`
  - Unknown items are cleaned up lazily when each inventory is first loaded, not at startup — your script can safely call `registerItem` at any time before the player's inventory is accessed, typically on resource start
  - You can combine `registerItem` with `registerUsableItem` to define both the item and its use behavior from an external script
  - If the item name already exists, registration is rejected to prevent overwriting file-defined items
  - Table fields (like `metadata`, `useOptions`, etc.) are deep-copied, so changes to the original table after registration have no effect
</Note>

## removeItem

Removes items from an inventory.

```lua
exports['jaksam_inventory']:removeItem(inventoryId, itemName, amount, metadata, slotId)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to remove items from. Can be a player server ID or inventory ID
</ParamField>

<ParamField path="itemName" type="string" required>
  The name of the item to remove
</ParamField>

<ParamField path="amount" type="number" required>
  How many items to remove
</ParamField>

<ParamField path="metadata" type="table">
  Metadata to match when removing items (if provided, only items with the same metadata AND name will be removed)
</ParamField>

<ParamField path="slotId" type="number">
  Specific slot to remove items from
</ParamField>

**Returns:**

- `success` (boolean) — true if items were removed successfully
- `resultCode` (string) — Error message if the operation failed

```lua
-- Remove 5 bread from player inventory
local success, result = exports['jaksam_inventory']:removeItem(1, 'bread', 5)

-- Remove specific weapon by metadata
local success, result = exports['jaksam_inventory']:removeItem(1, 'weapon_pistol', 1, {
    serial = "ABC123"
})

-- Remove from specific slot
local success, result = exports['jaksam_inventory']:removeItem(1, 'bread', 1, nil, 5)
```

## saveDirtyInventories

Saves all modified inventories to the database.

```lua
exports['jaksam_inventory']:saveDirtyInventories()
```

**Parameters:** None

**Returns:** `success` (boolean) — true if all inventories were saved successfully

```lua
-- Save all modified inventories
exports['jaksam_inventory']:saveDirtyInventories()

-- Good practice to save before server restart
AddEventHandler('onResourceStop', function(resourceName)
    if resourceName == GetCurrentResourceName() then
        exports['jaksam_inventory']:saveDirtyInventories()
    end
end)
```

## saveDirtyInventory

Saves a specific inventory to the database if it has been modified.

```lua
exports['jaksam_inventory']:saveDirtyInventory(inventoryId)
```

<ParamField path="inventoryId" type="string | number" required>
  The ID of the inventory to save
</ParamField>

**Returns:** `success` (boolean) — true if inventory was saved successfully

```lua
-- Save specific inventory
exports['jaksam_inventory']:saveDirtyInventory('police_stash_1')

-- Save player inventory after important changes
local success = exports['jaksam_inventory']:saveDirtyInventory(1)
if not success then
    print('Failed to save inventory')
end
```

## setInventoryMaxWeight

Sets the maximum weight capacity for an inventory.

```lua
exports['jaksam_inventory']:setInventoryMaxWeight(inventoryId, maxWeight)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID to modify
</ParamField>

<ParamField path="maxWeight" type="number" required>
  The new maximum weight capacity
</ParamField>

**Returns:** `success` (boolean) — true if weight was set successfully

```lua
-- Set player inventory max weight
exports['jaksam_inventory']:setInventoryMaxWeight(1, 100)

-- Set stash max weight
exports['jaksam_inventory']:setInventoryMaxWeight('police_stash_1', 500)
```

## setItemMetadataInSlot

Updates the metadata of an item in a specific inventory slot.

```lua
exports['jaksam_inventory']:setItemMetadataInSlot(inventoryId, slotId, metadata)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID containing the item
</ParamField>

<ParamField path="slotId" type="number" required>
  The slot containing the item to update
</ParamField>

<ParamField path="metadata" type="table" required>
  The new metadata to set
</ParamField>

**Returns:**

- `success` (boolean) — true if metadata was updated successfully
- `resultCode` (string) — Error message if the operation failed

```lua
-- Update weapon ammo
exports['jaksam_inventory']:setItemMetadataInSlot(1, 5, {
    serial = "ABC123",
    ammo = 6 -- update ammo count
})

-- Update item durability
exports['jaksam_inventory']:setItemMetadataInSlot(1, 3, {
    durability = 50
})
```

## setDurability

Sets the durability value of an item in a specific inventory slot.

```lua
exports['jaksam_inventory']:setDurability(inventoryId, slotId, durability)
```

<ParamField path="inventoryId" type="string | number" required>
  The inventory ID containing the item. Can be a player server ID or inventory ID
</ParamField>

<ParamField path="slotId" type="number" required>
  The slot containing the item to update
</ParamField>

<ParamField path="durability" type="number" required>
  The durability value to set (will be clamped between 0 and 100)
</ParamField>

**Returns:**

- `success` (boolean) — true if durability was updated successfully
- `resultCode` (string) — Error message if the operation failed

```lua
-- Set weapon durability to 75%
local success, result = exports['jaksam_inventory']:setDurability(1, 5, 75)

-- Decrease durability after weapon use
local item = exports['jaksam_inventory']:getItemFromSlot(playerId, slotId)
if item and item.metadata.durability then
    local newDurability = math.max(0, item.metadata.durability - 5)
    exports['jaksam_inventory']:setDurability(playerId, slotId, newDurability)
end

-- Set durability for stash item
exports['jaksam_inventory']:setDurability('police_stash_1', 3, 100)
```