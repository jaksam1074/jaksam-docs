---
title: "Shared"
icon: "circle-share-nodes"
description: "Exports that work on both server and client"
tag: "Updated"
---

## Compatibility

This script works with other popular inventory systems, like es_extended, qb-inventory, and ox_inventory.

<Info>
  For ESX and QBCore functions, the setup is done automatically. But, if you want to keep using exports from ox_inventory or qb-inventory for compatibility, you need to turn on this option in the file: `jaksam_inventory/integrations/sv_integrations.lua`
</Info>

## Shared functions

| Function | Description |
| --- | --- |
| [Get static items list](/jaksam-inventory/functions/shared/get-static-items-list) | Returns the list of all items in the inventory |
| [Get static item](/jaksam-inventory/functions/shared/get-static-item) | Gets generic item information (weight, stackable, description, etc.) |
| [Get item label](/jaksam-inventory/functions/shared/get-item-label) | Gets only the label (display name) of an item |
| [Get item image path](/jaksam-inventory/functions/shared/get-item-image-path) | Gets the NUI image path for an item |
