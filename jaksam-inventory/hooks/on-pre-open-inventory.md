---
title: "Pre open inventory"
description: "Hook triggered before a secondary inventory is sent to the client, can prevent it from opening."
icon: "door-open"
---

Triggered BEFORE a secondary inventory (stash, trunk, glovebox, shop, drop, container, another player's inventory, ...) is sent to the client. This hook can prevent the inventory from opening. Register with [`registerHook`](/jaksam-inventory/hooks#register-a-hook) using the event name `onPreOpenInventory`.

Opening your **own** player inventory never triggers this hook.

### Payload

| Field | Data Type | Description |
| --- | --- | --- |
| `playerId` | number | The player opening the inventory |
| `inventoryId` | string | e.g. `"stash_07ABC"` |
| `inventoryType` | string | `player`, `stash`, `shop`, `trunk`, `glovebox`, `container`, `ground_container`, `dumpster`, `omnipack` |
| `slotId` | number \| nil | Only for containers: the slot of the container item in the parent inventory |

<Note>
  This hook can prevent the inventory from opening by returning `false`. The data never leaves the server, so it is a real access control point (job/gang/whitelist gating), not just a UI check.
</Note>

**Available filters:** `inventoryTypeFilter` and `inventoryFilter`.

### Prefer stateless hooks

When a player presses the inventory key, the client preloads the inventories in range (stashes within 3m of a configured location, plus nearby trunks, gloveboxes, shops, dumpsters and drops) before the UI opens, and every preload triggers this hook. Your callback can therefore run several times for the same inventory, and for inventories the player never actually opens.

This only affects inventories that have configured coordinates - purely virtual ones, opened programmatically by your own script, are never preloaded. Still, write the callback as a pure check on job/gang/identifier where you can. A one-shot token pattern (`authorized[source] = inventoryId`, consumed on first match) is racy for a physically placed inventory: a preload can consume the token before the real open reaches the hook, and the open is then denied.

<Warning>
  The message returned by this hook is not shown to the player, because the preload would make it repeat. Call `notifyPlayer` from inside the hook if you want to tell the player why.
</Warning>

### Things to know

<AccordionGroup>
  <Accordion title="Private stashes">
    jaksam appends `_<ownerCharIdentifier>` to private stash IDs, so `payload.inventoryId` is the fully resolved ID. Prefix-based patterns keep matching, since the suffix is at the end.
  </Accordion>

  <Accordion title="Containers">
    Blocking a container only prevents it from being opened. Dropping an item onto a closed backpack still works, because that is an item transfer - use [`onItemTransferred`](/jaksam-inventory/hooks/on-item-transferred) to restrict what goes in.
  </Accordion>

  <Accordion title="forceOpenInventory still triggers this hook">
    `forceOpenInventory` skips jaksam's own permission checks, but not your hooks - the same as ox_inventory, whose `openInventory` hook fires even when `forceOpenInventory` passes `ignoreSecurityChecks`. This means a hook can block an admin `/openinventory`, `OpenInventoryById` or `forceOpenInventoryOX` too, so filter on the inventories you actually care about instead of denying by default.
  </Accordion>
</AccordionGroup>

### Examples

<AccordionGroup>
  <Accordion title="Restrict job stashes to their own job">
    ```lua
    -- Stateless check: safe to run repeatedly during the nearby-inventory preload
    exports['jaksam_inventory']:registerHook("onPreOpenInventory", function(payload)
        local job = payload.inventoryId:match("^job_stash_(.+)$")
        if job and GetPlayerJob(payload.playerId) ~= job then
            return false
        end
    end, {
        inventoryTypeFilter = {stash = true}
    })
    ```
  </Accordion>
</AccordionGroup>

See [Hooks overview](/jaksam-inventory/hooks) for the `registerHook` API, available filters, and return-value behavior.
