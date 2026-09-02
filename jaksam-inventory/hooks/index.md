---
title: "Hooks"
icon: "webhook"
description: "Intercept and modify inventory behavior with server-side hooks for item transfers, usage, and creation"
tag: "Updated"
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

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerHook(eventName, callback, options, priority)
```

</CodeGroup>

#### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `eventName` | string | The name of the hook event to listen for (see [Available Hook Events](#available-hook-events) below) |
| `callback` | function | The function to execute when the hook is triggered |
| `options` | table | Filters and configuration options (see [Options Parameter](#options-parameter) below) |
| `priority` | number | Execution priority (higher numbers execute first, default: 0) |

#### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `hookId` | string | Unique identifier for the registered hook (used to unregister the hook) |

### Unregister a Hook

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterHook(hookId)
```

</CodeGroup>

#### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `hookId` | string | The unique identifier returned when registering the hook |

### Unregister All Resource Hooks

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterResourceHooks(resourceName)
```

</CodeGroup>

#### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `resourceName` | string | Name of the resource to unregister all hooks for |

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
    For `onItemAdded`, `onItemRemoved`, `onInventoryCreated`, `onPreOpenInventory`, `onOmnipackTransaction`:

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

| Event | Description |
| --- | --- |
| [Item added](/jaksam-inventory/hooks/on-item-added) | Triggered when an item is added to an inventory |
| [Item removed](/jaksam-inventory/hooks/on-item-removed) | Triggered when an item is removed from an inventory |
| [Item transferred](/jaksam-inventory/hooks/on-item-transferred) | Triggered when an item is transferred between inventories |
| [Omnipack transaction](/jaksam-inventory/hooks/on-omnipack-transaction) | Triggered when an admin spawns or destroys an item through the admin inventory |
| [Pre use item](/jaksam-inventory/hooks/on-pre-use-item) | Triggered before an item is used, can cancel usage |
| [Post use item](/jaksam-inventory/hooks/on-post-use-item) | Triggered after an item has been used, notification-only |
| [Inventory created](/jaksam-inventory/hooks/on-inventory-created) | Triggered when a new inventory is created |
| [Pre open inventory](/jaksam-inventory/hooks/on-pre-open-inventory) | Triggered before a secondary inventory is opened, can prevent it from opening |

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

<Note>
  **Exception - [`onPreOpenInventory`](/jaksam-inventory/hooks/on-pre-open-inventory)**: the message is not shown to the player, because the preload would make it repeat. Call `notifyPlayer` from inside the hook if you want to tell the player why.
</Note>

## ox_inventory Compatibility

When the ox_inventory compatibility resource is installed, `exports.ox_inventory:registerHook(...)` is translated to the native hooks above, so ox_inventory scripts work without changes. Payloads are reshaped to the ox format, and ox option names (`itemFilter`, `typeFilter`, `inventoryFilter`, `print`) are translated as well.

| ox_inventory hook | Supported | Native hook used |
| --- | --- | --- |
| `createItem` | Yes | `onItemAdded` |
| `swapItems` | Yes | `onItemTransferred` |
| `openInventory` | Yes | `onPreOpenInventory` |
| `usingItem` | Yes | `onPreUseItem` |
| `buyItem` / `openShop` | No | no shop hooks yet |
| `craftItem` | No | no crafting hooks yet |

Registering an unsupported hook prints a warning and returns `nil` instead of throwing.

Three differences to be aware of when migrating:

- An ox hook can only allow or block; it cannot provide a custom message or notification type. Use the native hooks for that
- `openInventory` inherits the stateless requirement described in [`onPreOpenInventory`](/jaksam-inventory/hooks/on-pre-open-inventory)
- **Player inventories are identified differently.** ox hooks receive the player's server ID as a number (`inventoryId = 4`), matching ox_inventory. Native hooks receive jaksam's character identifier as a string (`inventoryId = "char1:35030084..."`). Every other inventory type uses the same string ID in both
