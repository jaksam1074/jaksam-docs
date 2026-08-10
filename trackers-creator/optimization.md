---
title: "Optimization"
description: "Hook into your inventory's item events to improve Trackers Creator performance."
icon: "gauge-high"
---

This page shows you how to optimize the script. Following all the instructions below will improve the script's performance.

## Item check

Use these **server-side** events right after any item addition/removal. They can be used anywhere, as long as you replace the parameters with the proper ones.

```lua
TriggerEvent("framework:onItemAdded", playerId, itemName, itemCount)
```

```lua
TriggerEvent("framework:onItemRemoved", playerId, itemName, itemCount)
```

### Examples

<Note>
  If you use something that is not listed in the examples, editing it is up to you — the events listed above work anywhere if used properly.
</Note>

#### ESX

<Info>
  Default ESX already has `esx:onAddInventoryItem` and `esx:onRemoveInventoryItem`, which means you won't need to add anything. Only follow the example below if you don't have those events for any reason.
</Info>

Go to `es_extended/server/classes/player.lua` and add the following code:

<Frame>
  ![ESX item added/removed hook example 1](/images/immagine-2-1.png)
</Frame>

<Frame>
  ![ESX item added/removed hook example 2](/images/immagine-3.png)
</Frame>

#### OX Inventory (ESX)

Go to `es_extended/server/classes/overrides/oxinventory.lua` and add the following code:

<Frame>
  ![OX Inventory hook example 1](/images/immagine-4-1.png)
</Frame>

<Frame>
  ![OX Inventory hook example 2](/images/immagine.png)
</Frame>

#### QBCore (latest version)

Go to `qb-inventory/server/main.lua` and add the following code:

<Frame>
  ![QBCore hook example 1](/images/immagine-5-1.png)
</Frame>

<Frame>
  ![QBCore hook example 2](/images/immagine-6.png)
</Frame>
