---
title: "Item added"
description: "Hook triggered when an item is added to an inventory."
icon: "circle-plus"
---

Triggered when an item is added to an inventory. Register with [`registerHook`](/jaksam-inventory/hooks#register-a-hook) using the event name `onItemAdded`.

### Payload

| Field | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string | e.g. `"player:1"` |
| `itemName` | string | e.g. `"bread"` |
| `amount` | number | Amount added |
| `metadata` | table \| nil | Item metadata, can be nil |
| `slotId` | number | Slot the item was added to |

### Examples

<AccordionGroup>
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
</AccordionGroup>

See [Hooks overview](/jaksam-inventory/hooks) for the `registerHook` API, available filters, and return-value behavior.
