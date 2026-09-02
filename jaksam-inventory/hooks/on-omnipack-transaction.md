---
title: "Omnipack transaction"
description: "Hook triggered when an admin spawns or destroys an item through the admin inventory (omnipack)."
icon: "user-shield"
---

Triggered when an admin takes an item out of the [admin inventory (omnipack)](/jaksam-inventory/guides/admin-inventory), which creates it, or drags one into it, which destroys it. This hook can cancel the operation. Register with [`registerHook`](/jaksam-inventory/hooks#register-a-hook) using the event name `onOmnipackTransaction`.

It is the only hook that knows **which** admin did it, so it is the one to use to log admin item spawns.

### Payload

| Field | Data Type | Description |
| --- | --- | --- |
| `playerId` | number | The admin using the admin inventory |
| `action` | string | `"spawn"` (item created) or `"delete"` (item destroyed) |
| `inventoryId` | string | The other inventory: where the item goes, or where it comes from |
| `slotId` | number | The slot involved in the other inventory |
| `itemName` | string | e.g. `"weapon_pistol"` |
| `amount` | number | Amount created or destroyed |
| `metadata` | table \| nil | Item metadata |

<Note>
  The admin inventory does **not** trigger [`onItemTransferred`](/jaksam-inventory/hooks/on-item-transferred), it only triggers this hook. This way the restrictions you write for your players are never applied to an admin spawning an item.
</Note>

**Available filters:** `itemNameFilter`, `itemTypeFilter`, `inventoryTypeFilter` and `inventoryFilter` - the last two apply to `inventoryId`, so the omnipack itself is never what you filter on.

### Examples

<AccordionGroup>
  <Accordion title="Log what admins spawn from the admin inventory">
    ```lua
    exports['jaksam_inventory']:registerHook("onOmnipackTransaction", function(payload)
        print(("[ADMIN] %s (%s) %sed %dx %s - inventory: %s"):format(
            GetPlayerName(payload.playerId), payload.playerId, payload.action,
            payload.amount, payload.itemName, payload.inventoryId))
    end)
    ```
  </Accordion>

  <Accordion title="Stop admins from spawning a specific item">
    ```lua
    exports['jaksam_inventory']:registerHook("onOmnipackTransaction", function(payload)
        if payload.action ~= "spawn" then return end -- Deleting it is fine

        return false, "This item can't be spawned from the admin inventory"
    end, {
        itemNameFilter = {money = true}
    })
    ```
  </Accordion>
</AccordionGroup>

See [Hooks overview](/jaksam-inventory/hooks) for the `registerHook` API, available filters, and return-value behavior.
