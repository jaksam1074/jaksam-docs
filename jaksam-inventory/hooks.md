---
title: "Hooks"
icon: "webhook"
description: "Intercept and modify inventory behavior with server-side hooks for item transfers, usage, and creation"
---

Hooks are a way to modify the behavior of the inventory system. They are registered on the server and can be used to modify the behavior of the inventory system, for example to prevent players from moving items to a specific inventory. There are some examples of hooks in the `jaksam_inventory/_hooks` folder.

## Best Practices

<CardGroup cols={3}>
  <Card title="Use filters" icon="filter">
    Always use appropriate filters to avoid unnecessary hook executions
  </Card>

  <Card title="Early returns" icon="right-from-bracket">
    Use early returns to exit hooks when conditions aren't met
  </Card>

  <Card title="Performance" icon="gauge-high">
    Keep hook logic lightweight to avoid impacting inventory performance
  </Card>
</CardGroup>

## Use Case Examples

- Prevent players from stealing items that have the `sole_owner` metadata field (e.g., VIP items)
- Prevent players from moving police weapons into their personal inventory
- Allow only one backpack per player inventory
- Crafting items by dragging a specific item over another item (for example dragging bread on meat can make a sandwich)
- Block item usage when player is handcuffed or in specific zones
- Track item usage statistics and achievements
- Prevent using certain items while in vehicles
- Add starter items to new player inventories when they are created
- Pre-populate dumpsters or stashes with random items on creation

## API Functions

### Register a Hook

```lua
exports['jaksam_inventory']:registerHook(eventName, callback, options, priority)
```

<ParamField path="eventName" type="string" required>
  The name of the hook event to listen for (list of available events below)
</ParamField>

<ParamField path="callback" type="function" required>
  The function to execute when the hook is triggered
</ParamField>

<ParamField path="options" type="table">
  Filters and configuration options (list of available options below)
</ParamField>

<ParamField path="priority" type="number">
  Execution priority (higher numbers execute first, default: 0)
</ParamField>

**Returns:** `hookId` (string) — Unique identifier for the registered hook (used to unregister the hook)

### Unregister a Hook

```lua
exports['jaksam_inventory']:unregisterHook(hookId)
```

<ParamField path="hookId" type="string" required>
  The unique identifier returned when registering the hook
</ParamField>

### Unregister All Resource Hooks

```lua
exports['jaksam_inventory']:unregisterResourceHooks(resourceName)
```

<ParamField path="resourceName" type="string" required>
  Name of the resource to unregister all hooks for
</ParamField>

## Options Parameter

The options parameter accepts a table with filters to optimize performance.

<Tabs>
  <Tab title="Common (all events)">
    ```lua
        local options = {
            -- Debug: Print to console when hook triggers
            print = true,
    
            -- Only trigger for specific items
            itemNameFilter = {
                bread = true,
                weapon_pistol = true
            },
    
            -- Only trigger for specific item types
            itemTypeFilter = {
                weapon = true,
                currency = true
            }
        }
    ```
  </Tab>
  <Tab title="Inventory filters">
    For `onItemAdded`, `onItemRemoved`, `onInventoryCreated`:

    ```lua
        local options = {
            -- Filter by inventory type (recommended)
            inventoryTypeFilter = {
                player = true,
                stash = true
            },
    
            -- Filter by specific inventory patterns (advanced)
            inventoryFilter = {
                "player:.*",      -- All players
                "stash_police"    -- Specific stash
            }
        }
    ```
  </Tab>
  <Tab title="Transfer filters">
    For `onItemTransferred` only:

    ```lua
        local options = {
            -- Filter source inventory by type
            inventoryFromTypeFilter = { player = true },
    
            -- Filter source inventory by name pattern
            inventoryFromFilter = {
                "player:.*",      -- All players
                "vehicle:123"     -- Specific vehicle
            },
    
            -- Filter destination inventory by type
            inventoryToTypeFilter = { stash = true },
    
            -- Filter destination inventory by name pattern
            inventoryToFilter = {
                "stash_police",   -- Specific stash
                "container:.*"    -- All containers
            },
    
            -- Only intra-inventory moves (drag within same inventory)
            intraInventoryOnly = true
        }
    ```
  </Tab>
</Tabs>

## Available Hook Events

### onItemAdded

Triggered when an item is added to an inventory.

**Payload:**

```lua
payload = {
    inventoryId = "player:1",
    itemName = "bread",
    amount = 5,
    metadata = {durability = 100}, -- Item metadata (can be nil)
    slotId = 1,
}
```

### onItemRemoved

Triggered when an item is removed from an inventory.

**Payload:**

```lua
payload = {
    inventoryId = "player:1",
    itemName = "bread",
    amount = 3,
    metadata = {durability = 80},
    slotId = 1
}
```

### onItemTransferred

Triggered when an item is transferred between inventories (including intra-inventory moves).

**Payload:**

```lua
payload = {
    playerId = 1,
    inventoryIdFrom = "player:1",
    inventoryIdTo = "stash_police",
    slotIdFrom = 1,
    slotIdTo = 5,
    itemName = "weapon_pistol",
    amount = 1,
    metadata = {ammo = 12}
}
```

### onPreUseItem

Triggered BEFORE an item is used (before consume, animations, and delays). This hook can cancel item usage.

**Execution Order:** After `STATIC_ITEM.canUse` and `oxServerExport 'usingItem'`, before consume

**Payload:**

```lua
payload = {
    playerId = 1,
    inventoryId = "license:abcd1234",
    slotId = 3,
    itemName = "bread",
    metadata = {durability = 80}
}
```

<Note>
  This hook can prevent item usage by returning `false`. Useful for global item usage restrictions (e.g., handcuffed players, vehicle restrictions, zone restrictions).
</Note>

### onPostUseItem

Triggered AFTER an item has been used (after consume, animations, delays, and all callbacks).

**Execution Order:** At the very end of the item usage process, after `oxServerExport 'usedItem'`

**Payload:**

```lua
payload = {
    playerId = 1,
    inventoryId = "license:abcd1234",
    slotId = 3,
    itemName = "bread",
    metadata = {durability = 80}
}
```

<Note>
  This hook is notification-only and cannot cancel item usage. Useful for logging, statistics, achievements, and triggering external systems.
</Note>

### onInventoryCreated

Triggered when a new inventory is created.

**Payload:**

```lua
payload = {
    inventoryId = "stash_police",
    inventoryType = "stash",
    label = "Police Stash",
    options = {maxWeight = 100, maxSlots = 50}, -- May be nil if not explicitly set, if so, it will follow the config for global inventories options
    items = {},
    metadata = {}
}
```

<Note>
  This hook is notification-only and cannot cancel inventory creation. Useful for adding starter items, pre-populating inventories with random loot, or logging inventory creation. Use exports to add items to the inventory within the callback.
</Note>

**Available Filters:**

- `inventoryTypeFilter`: Filter by inventory type (player, stash, trunk, dumpster, etc.)
- `inventoryFilter`: Filter by specific inventory ID patterns

## Hook Behavior

<CardGroup cols={2}>
  <Card title="Priority" icon="arrow-up-1-9">
    Higher numbers execute first (default: 0)
  </Card>

  <Card title="Return values" icon="reply">
    `return nil` or `return true`: allow the action to continue.

    `return false, "message", "notifyType"`: prevents the action and stops further hook execution. The message and notifyType parameters are optional (notifyType can be `"error"`, `"success"`, `"info"`)
  </Card>
</CardGroup>

## Quick Examples

<AccordionGroup>
  <Accordion title="Block police weapons in player inventory">
    ```lua
        exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
            local item = exports["jaksam_inventory"]:getStaticItem(payload.itemName)
            if item and item.policeOnly then
                return false, "Only police can have this weapon"
            end
        end, {
            itemTypeFilter = {weapon = true},
            inventoryToTypeFilter = {player = true}
        })
    ```
  </Accordion>

  <Accordion title="One backpack per player">
    ```lua
        exports['jaksam_inventory']:registerHook("onItemAdded", function(payload)
            local backpackCount = exports["jaksam_inventory"]:getTotalItemAmount(payload.inventoryId, "backpack")
            if backpackCount >= 1 then
                return false, "You can only have one backpack"
            end
        end, {
            itemNameFilter = {backpack = true},
            inventoryTypeFilter = {player = true}
        })
    ```
  </Accordion>

  <Accordion title="Simple crafting (drag items together)">
    ```lua
        exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
            local sourceItem = exports["jaksam_inventory"]:getItemFromSlot(payload.inventoryIdFrom, payload.slotIdFrom)
            local targetItem = exports["jaksam_inventory"]:getItemFromSlot(payload.inventoryIdTo, payload.slotIdTo)
            if not targetItem then return end -- Dragged over an empty slot
    
            if sourceItem.name == "bread" and targetItem.name == "meat" then
                exports["jaksam_inventory"]:removeItem(payload.inventoryIdFrom, "bread", 1, payload.slotIdFrom)
                exports["jaksam_inventory"]:removeItem(payload.inventoryIdFrom, "meat", 1, payload.slotIdTo)
                exports["jaksam_inventory"]:addItem(payload.inventoryIdFrom, "sandwich", 1)
                return false, "You crafted a sandwich", "success"
            end
        end, {intraInventoryOnly = true})
    ```
  </Accordion>

  <Accordion title="Filter by specific inventory name">
    ```lua
        -- Only trigger when items are added to police stash
        exports['jaksam_inventory']:registerHook("onItemAdded", function(payload)
            print("Item added to police stash:", payload.itemName)
        end, {
            inventoryFilter = {"stash_police"}
        })
    ```
  </Accordion>

  <Accordion title="Block item usage when handcuffed">
    ```lua
        exports['jaksam_inventory']:registerHook("onPreUseItem", function(payload)
            if IsPlayerHandcuffed(payload.playerId) then
                return false, "You cannot use items while handcuffed"
            end
        end)
    ```
  </Accordion>

  <Accordion title="Block food usage in vehicles">
    ```lua
        exports['jaksam_inventory']:registerHook("onPreUseItem", function(payload)
            local ped = GetPlayerPed(payload.playerId)
            if IsPedInAnyVehicle(ped, false) then
                return false, "You cannot eat while driving", "warning"
            end
        end, {
            itemTypeFilter = {food = true}
        })
    ```
  </Accordion>

  <Accordion title="Log all item usage">
    ```lua
        exports['jaksam_inventory']:registerHook("onPostUseItem", function(payload)
            print(("Player %d used %s"):format(payload.playerId, payload.itemName))
            -- Send to external logging system, database, etc.
        end)
    ```
  </Accordion>

  <Accordion title="Track food consumption statistics">
    ```lua
        local foodStats = {}
    
        exports['jaksam_inventory']:registerHook("onPostUseItem", function(payload)
            foodStats[payload.itemName] = (foodStats[payload.itemName] or 0) + 1
            print("Total", payload.itemName, "consumed:", foodStats[payload.itemName])
        end, {
            itemTypeFilter = {food = true}
        })
    ```
  </Accordion>

  <Accordion title="Add starter items to new player inventories">
    ```lua
        exports['jaksam_inventory']:registerHook("onInventoryCreated", function(payload)
            exports["jaksam_inventory"]:addItem(payload.inventoryId, "bread", 5)
            exports["jaksam_inventory"]:addItem(payload.inventoryId, "water", 3)
            exports["jaksam_inventory"]:addItem(payload.inventoryId, "phone", 1)
        end, {
            inventoryTypeFilter = {player = true}
        })
    ```
  </Accordion>

  <Accordion title="Populate dumpsters with random loot">
    <Note>
      An existing hook for this is already provided in the `_hooks` folder of jaksam_inventory.
    </Note>

    ```lua
        -- Loot table: each entry has itemName, minAmount, maxAmount
        local lootTable = {
            {name = "trash", min = 1, max = 5},
            {name = "newspaper", min = 1, max = 2},
            {name = "bottle", min = 1, max = 3},
            {name = "sandwich", min = 1, max = 1},
            {name = "bandage", min = 1, max = 2},
        }
    
        -- Min and max number of different items per dumpster
        local minItems, maxItems = 1, 3
    
        -- Fisher-Yates shuffle for random selection without repetition
        local function shuffleTable(tbl)
            local shuffled = {}
            for i = 1, #tbl do shuffled[i] = tbl[i] end
            for i = #shuffled, 2, -1 do
                local j = math.random(1, i)
                shuffled[i], shuffled[j] = shuffled[j], shuffled[i]
            end
            return shuffled
        end
    
        exports['jaksam_inventory']:registerHook("onInventoryCreated", function(payload)
            local itemCount = math.random(minItems, math.min(maxItems, #lootTable))
            local shuffledLoot = shuffleTable(lootTable)
    
            for i = 1, itemCount do
                local loot = shuffledLoot[i]
                local amount = math.random(loot.min, loot.max)
                exports["jaksam_inventory"]:addItem(payload.inventoryId, loot.name, amount)
            end
        end, {
            inventoryTypeFilter = {dumpster = true}
        })
    ```
  </Accordion>
</AccordionGroup>