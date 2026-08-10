---
title: "Pre use item"
description: "Hook triggered before an item is used, can cancel the usage."
icon: "hand"
---

Triggered BEFORE an item is used (before consume, animations, and delays). This hook can cancel item usage. Register with [`registerHook`](/jaksam-inventory/hooks#register-a-hook) using the event name `onPreUseItem`.

**Execution order:** after `STATIC_ITEM.canUse` and `oxServerExport 'usingItem'`, before consume.

### Payload

| Field | Data Type | Description |
| --- | --- | --- |
| `playerId` | number | The player using the item |
| `inventoryId` | string | e.g. `"license:abcd1234"` |
| `slotId` | number | Slot of the item being used |
| `itemName` | string | e.g. `"bread"` |
| `metadata` | table \| nil | Item metadata |

<Note>
  This hook can prevent item usage by returning `false`. Useful for global item usage restrictions (e.g., handcuffed players, vehicle restrictions, zone restrictions).
</Note>

### Examples

<AccordionGroup>
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
</AccordionGroup>

See [Hooks overview](/jaksam-inventory/hooks) for the `registerHook` API, available filters, and return-value behavior.
