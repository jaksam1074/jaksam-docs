---
title: "Commands"
icon: "slash-forward"
description: "Full list of admin commands for managing items, inventories, and stashes"
---

# Admin Commands

<Note>
  All admin commands require **ACE permission**. Use `/inventory` to check if you have it.
</Note>

## `/inventory`

Opens the admin menu to manage items, shops, stashes, view statistics, etc.

## `/giveitem`

Give items to a player or inventory.

<ParamField path="inventoryId|playerId|'me'" type="string" required>
  Target inventory, player ID, or `me` for yourself
</ParamField>

<ParamField path="itemName" type="string" required>
  Name of the item to give
</ParamField>

<ParamField path="amount" type="number" required>
  Quantity to give
</ParamField>

<ParamField path="slotId" type="number">
  Optional specific slot to place the item in
</ParamField>

```bash
/giveitem me bread 10                     # Give 10 bread to yourself
/giveitem 1 water 5                       # Give 5 water to player 1
/giveitem stash_police weapon_pistol 1 3  # Give 1 weapon_pistol to stash_police in slot 3
```

## `/removeitem`

Remove items from a player or inventory.

<ParamField path="inventoryId" type="string" required>
  Target inventory or player ID
</ParamField>

<ParamField path="itemName" type="string" required>
  Name of the item to remove
</ParamField>

<ParamField path="amount" type="number" required>
  Quantity to remove
</ParamField>

<ParamField path="slotId" type="number">
  Optional specific slot to remove from
</ParamField>

```bash
/removeitem 1 bread 10                    # Remove 10 bread from player 1's inventory
/removeitem stash_police weapon_pistol 1  # Remove 1 weapon_pistol from stash_police
```

## `/clearinventory`

Clear all items from an inventory. If `inventoryId` is empty, clears your own inventory. You can also exclude an item from clearing.

<ParamField path="inventoryId" type="string">
  Target inventory. Defaults to your own inventory if omitted
</ParamField>

<ParamField path="excludedItemName" type="string">
  Item to keep, excluded from clearing
</ParamField>

```bash
/clearinventory          # Clear your inventory
/clearinventory 1        # Clear player 1's inventory
/clearinventory 2 phone  # Clear player 2's inventory but keep phone
```

## `/openinventory`

Open another player's inventory.

<ParamField path="targetPlayerId" type="number" required>
  ID of the player whose inventory to open
</ParamField>

```bash
/openinventory 1  # Open player 1's inventory
```

## `/saveinventories`

Force save all modified inventories to database.

<CardGroup cols={2}>
  <Card title="Inventory Management" icon="box-open">
    `/inventory`, `/giveitem`, `/removeitem`, `/clearinventory`
  </Card>

  <Card title="Player Actions" icon="user">
    `/openinventory`, `/saveinventories`
  </Card>
</CardGroup>