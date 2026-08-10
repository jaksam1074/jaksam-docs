---
title: "Item transferred"
description: "Hook triggered when an item is transferred between inventories, including intra-inventory moves."
icon: "right-left"
---

Triggered when an item is transferred between inventories (including intra-inventory moves, e.g. dragging within the same inventory). Register with [`registerHook`](/jaksam-inventory/hooks#register-a-hook) using the event name `onItemTransferred`.

### Payload

| Field | Data Type | Description |
| --- | --- | --- |
| `playerId` | number | The player performing the transfer |
| `inventoryIdFrom` | string | Source inventory ID |
| `inventoryIdTo` | string | Destination inventory ID |
| `slotIdFrom` | number | Source slot |
| `slotIdTo` | number | Destination slot |
| `itemName` | string | e.g. `"weapon_pistol"` |
| `amount` | number | Amount transferred |
| `metadata` | table \| nil | Item metadata |

### Examples

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
</AccordionGroup>

See [Hooks overview](/jaksam-inventory/hooks) for the `registerHook` API, available filters (including the transfer-specific `inventoryFromTypeFilter`/`inventoryToTypeFilter`/`intraInventoryOnly`), and return-value behavior.
