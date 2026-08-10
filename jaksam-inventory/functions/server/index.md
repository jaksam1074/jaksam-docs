---
title: "Server"
icon: "server"
description: "Full reference of server-side exports for managing inventories, items, stashes, and vehicles"
tag: "Updated"
---

## Compatibility

This script works with other popular inventory systems, like es_extended, qb-inventory, and ox_inventory.

<Info>
  For ESX and QBCore functions, the setup is done automatically. But, if you want to keep using exports from ox_inventory or qb-inventory for compatibility, you need to turn on this option in the file: `jaksam_inventory/integrations/sv_integrations.lua`
</Info>

## Server functions

| Function | Description |
| --- | --- |
| [Add item](/jaksam-inventory/functions/server/add-item) | Adds items to an inventory |
| [Add item to trunk](/jaksam-inventory/functions/server/add-item-to-trunk) | Adds items to a vehicle trunk by plate |
| [Add item to glovebox](/jaksam-inventory/functions/server/add-item-to-glovebox) | Adds items to a vehicle glovebox by plate |
| [Remove item from trunk](/jaksam-inventory/functions/server/remove-item-from-trunk) | Removes items from a vehicle trunk by plate |
| [Remove item from glovebox](/jaksam-inventory/functions/server/remove-item-from-glovebox) | Removes items from a vehicle glovebox by plate |
| [Get inventory ID from plate](/jaksam-inventory/functions/server/get-inventory-id-from-plate) | Resolves the full inventory ID for a vehicle compartment |
| [Can carry item](/jaksam-inventory/functions/server/can-carry-item) | Checks if an inventory has space for additional items |
| [Can swap item](/jaksam-inventory/functions/server/can-swap-item) | Checks if swapping two items is possible |
| [Clear inventory](/jaksam-inventory/functions/server/clear-inventory) | Removes all items from an inventory |
| [Create inventory](/jaksam-inventory/functions/server/create-inventory) | Creates a new inventory in database and/or memory |
| [Force open inventory](/jaksam-inventory/functions/server/force-open-inventory) | Forces an inventory open for a specific player |
| [Get inventory](/jaksam-inventory/functions/server/get-inventory) | Gets complete data about an inventory |
| [Get item from slot](/jaksam-inventory/functions/server/get-item-from-slot) | Gets an item from a specific slot |
| [Get item by name](/jaksam-inventory/functions/server/get-item-by-name) | Gets the first item found by name |
| [Get items by name](/jaksam-inventory/functions/server/get-items-by-name) | Gets all items found by name |
| [Get item label](/jaksam-inventory/functions/server/get-item-label) | Gets the display label of an item |
| [Get total item amount](/jaksam-inventory/functions/server/get-total-item-amount) | Returns the total amount of an item, including containers |
| [Has item](/jaksam-inventory/functions/server/has-item) | Checks if an inventory has a specific item |
| [Register usable item](/jaksam-inventory/functions/server/register-usable-item) | Registers a callback for when an item is used |
| [Register stash](/jaksam-inventory/functions/server/register-stash) | Dynamically registers a new stash |
| [Register item](/jaksam-inventory/functions/server/register-item) | Registers a new item definition at runtime |
| [Remove item](/jaksam-inventory/functions/server/remove-item) | Removes items from an inventory |
| [Save dirty inventories](/jaksam-inventory/functions/server/save-dirty-inventories) | Saves all modified inventories to the database |
| [Save dirty inventory](/jaksam-inventory/functions/server/save-dirty-inventory) | Saves a specific inventory to the database |
| [Set inventory max weight](/jaksam-inventory/functions/server/set-inventory-max-weight) | Sets the maximum weight capacity for an inventory |
| [Set item metadata in slot](/jaksam-inventory/functions/server/set-item-metadata-in-slot) | Updates the metadata of an item in a slot |
| [Set durability](/jaksam-inventory/functions/server/set-durability) | Sets the durability value of an item in a slot |
