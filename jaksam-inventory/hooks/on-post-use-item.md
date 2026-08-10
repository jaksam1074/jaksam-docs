---
title: "Post use item"
description: "Hook triggered after an item has been used, notification-only."
icon: "circle-check"
---

Triggered AFTER an item has been used (after consume, animations, delays, and all callbacks). Register with [`registerHook`](/jaksam-inventory/hooks#register-a-hook) using the event name `onPostUseItem`.

**Execution order:** at the very end of the item usage process, after `oxServerExport 'usedItem'`.

### Payload

| Field | Data Type | Description |
| --- | --- | --- |
| `playerId` | number | The player who used the item |
| `inventoryId` | string | e.g. `"license:abcd1234"` |
| `slotId` | number | Slot of the item that was used |
| `itemName` | string | e.g. `"bread"` |
| `metadata` | table \| nil | Item metadata |

<Note>
  This hook is notification-only and cannot cancel item usage. Useful for logging, statistics, achievements, and triggering external systems.
</Note>

### Examples

<AccordionGroup>
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
</AccordionGroup>

See [Hooks overview](/jaksam-inventory/hooks) for the `registerHook` API, available filters, and return-value behavior.
