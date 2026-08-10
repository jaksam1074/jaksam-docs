---
title: "Client"
icon: "laptop"
description: "Client-side exports for reading and controlling the inventory"
tag: "Updated"
---

## Compatibility

This script works with other popular inventory systems, like es_extended, qb-inventory, and ox_inventory.

<Info>
  For ESX and QBCore functions, the setup is done automatically. But, if you want to keep using exports from ox_inventory or qb-inventory for compatibility, you need to turn on this option in the file: `jaksam_inventory/integrations/sv_integrations.lua`
</Info>

## Client functions

| Function | Description |
| --- | --- |
| [Get total item amount](/jaksam-inventory/functions/client/get-total-item-amount) | Gets the total amount of a specific item in the player's inventory |
| [Open inventory](/jaksam-inventory/functions/client/open-inventory) | Opens an inventory alongside the player's inventory |
| [Close inventory](/jaksam-inventory/functions/client/close-inventory) | Closes the inventory UI |
| [Get inventory](/jaksam-inventory/functions/client/get-inventory) | Gets the player's self inventory |
| [Get item by name](/jaksam-inventory/functions/client/get-item-by-name) | Gets the first item found in the player's self inventory by name |
| [Get items by name](/jaksam-inventory/functions/client/get-items-by-name) | Gets all items matching a name from the player's self inventory |
| [Get item from slot](/jaksam-inventory/functions/client/get-item-from-slot) | Gets an item from a specific slot in the player's inventory |
| [Show hotbar](/jaksam-inventory/functions/client/show-hotbar) | Shows the hotbar UI with the first 5 slots |
| [Set hotbar disabled](/jaksam-inventory/functions/client/set-hotbar-disabled) | Enables or disables the hotbar functionality |
| [Set hotkeys enabled](/jaksam-inventory/functions/client/set-hotkeys-enabled) | Enables or disables the hotkeys (slots 1-5) |
| [Are hotkeys enabled](/jaksam-inventory/functions/client/are-hotkeys-enabled) | Returns whether hotkeys are currently enabled |
| [Dequip weapon](/jaksam-inventory/functions/client/dequip-weapon) | Dequips the currently equipped weapon |
| [Set weapon wheel](/jaksam-inventory/functions/client/set-weapon-wheel) | Enables or disables the default GTA5 weapon wheel |
| [Set jaksam weapon wheel](/jaksam-inventory/functions/client/set-jaksam-weapon-wheel) | Enables or disables the jaksam radial weapon wheel |
| [Register action button](/jaksam-inventory/functions/client/register-action-button) | Registers a custom action button in the inventory toolbar |
| [Unregister action button](/jaksam-inventory/functions/client/unregister-action-button) | Removes a previously registered action button |
| [Show action button](/jaksam-inventory/functions/client/show-action-button) | Makes a hidden action button visible |
| [Hide action button](/jaksam-inventory/functions/client/hide-action-button) | Hides an action button without removing it |
| [Get vehicle inventory limits](/jaksam-inventory/functions/client/get-vehicle-inventory-limits) | Returns trunk/glovebox limits for a vehicle |
| [Is inventory open](/jaksam-inventory/functions/client/is-inventory-open) | Checks if an inventory is currently open |
| [Set inventory disabled](/jaksam-inventory/functions/client/set-inventory-disabled) | Completely disables or re-enables inventory opening |
| [Is inventory disabled](/jaksam-inventory/functions/client/is-inventory-disabled) | Returns whether inventory opening is currently disabled |
