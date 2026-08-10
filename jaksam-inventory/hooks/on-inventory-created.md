---
title: "Inventory created"
description: "Hook triggered when a new inventory is created, notification-only."
icon: "wand-magic-sparkles"
---

Triggered when a new inventory is created. Register with [`registerHook`](/jaksam-inventory/hooks#register-a-hook) using the event name `onInventoryCreated`.

### Payload

| Field | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string | e.g. `"stash_police"` |
| `inventoryType` | string | e.g. `"stash"` |
| `label` | string | e.g. `"Police Stash"` |
| `options` | table \| nil | May be nil if not explicitly set, in which case it follows the config for global inventory options |
| `items` | table | Items in the inventory at creation |
| `metadata` | table | Additional inventory metadata |

<Note>
  This hook is notification-only and cannot cancel inventory creation. Useful for adding starter items, pre-populating inventories with random loot, or logging inventory creation. Use exports to add items to the inventory within the callback.
</Note>

**Available filters:** `inventoryTypeFilter` (filter by inventory type: player, stash, trunk, dumpster, etc.), `inventoryFilter` (filter by specific inventory ID patterns).

### Examples

<AccordionGroup>
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

See [Hooks overview](/jaksam-inventory/hooks) for the `registerHook` API, available filters, and return-value behavior.
