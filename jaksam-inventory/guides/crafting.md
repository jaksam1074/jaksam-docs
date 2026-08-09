---
title: "Crafting Recipes (Drag & Drop)"
icon: "flask-gear"
description: "Let players craft items by dragging one item over another using the built-in crafting hook"
---

Want players to craft items by dragging one item over another? This guide shows you how, step-by-step.

This feature allows players to craft items by dragging a source item over a target item in the same inventory. When the recipe matches, the items are combined and the result is created.

<Note>
  This functionality is provided by the `_hooks/sv_craftings.lua` hook. You just need to add your recipes to the `CRAFTING_RECIPES` table.
</Note>

## How it works

<Steps>
  <Step title="Drag source onto target">
    Player drags a **source item** over a **target item** in the same inventory.
  </Step>
  <Step title="Recipe check">
    The system checks if there's a matching recipe.
  </Step>
  <Step title="Crafting happens">
    If the recipe matches and quantities are sufficient, the crafting happens.
  </Step>
  <Step title="Items are consumed">
    Source and/or target items are removed (based on recipe settings).
  </Step>
  <Step title="Result is added">
    The result item is added to the inventory.
  </Step>
</Steps>

## Step-by-step guide

<Steps>
  <Step title="Open the crafting hook">
    Navigate to: `jaksam_inventory/_hooks/sv_craftings.lua`
  </Step>
  <Step title="Find the recipes table">
    Find the `CRAFTING_RECIPES` table (it's near the top of the file).
  </Step>
  <Step title="Add your recipe">
    Add your recipe following this format:

    ```lua
        local CRAFTING_RECIPES = {
            ["source_item_name"] = {
                sourceQuantityRequired = 1,        -- How many source items needed
                sourceIsToRemove = true,           -- Remove source item after crafting?
                targetItem = "target_item_name",  -- Name of the target item
                targetQuantity = 1,                -- How many target items needed
                targetIsToRemove = true,           -- Remove target item after crafting?
                resultItem = "result_item_name",  -- Name of the item created
                resultQuantity = 1,                -- How many result items created
            },
        }
    ```
  </Step>
  <Step title="Restart">
    Save the file and restart the script/reload the server.
  </Step>
</Steps>

<Tip>
  That's it! Now players can drag the source item over the target item to craft.
</Tip>

## Recipe properties explained

<ParamField path="sourceQuantityRequired" type="number">
  How many of the source item are needed for the recipe
</ParamField>

<ParamField path="sourceIsToRemove" type="boolean">
  Set to `true` if the source item should be removed after crafting, `false` to keep it
</ParamField>

<ParamField path="targetItem" type="string">
  The exact name (as defined in `items.lua`) of the item you drag the source item onto
</ParamField>

<ParamField path="targetQuantity" type="number">
  How many of the target item are needed for the recipe
</ParamField>

<ParamField path="targetIsToRemove" type="boolean">
  Set to `true` if the target item should be removed after crafting, `false` to keep it
</ParamField>

<ParamField path="resultItem" type="string">
  The exact name (as defined in `items.lua`) of the item that will be created
</ParamField>

<ParamField path="resultQuantity" type="number">
  How many result items will be created
</ParamField>

## Examples

<Tabs>
  <Tab title="Upgrade scope to thermal">
    Combine a wrench with an advanced scope to create a thermal scope:

    ```lua
        ["weapon_wrench"] = {
            sourceQuantityRequired = 1,
            sourceIsToRemove = false,              -- Keep the wrench (reusable tool)
            targetItem = "advanced_scope",
            targetQuantity = 1,
            targetIsToRemove = true,               -- Remove the advanced scope
            resultItem = "thermal_scope",
            resultQuantity = 1,
        },
    ```

    **How to use:** Drag the wrench over the advanced scope → thermal scope is created, wrench stays, advanced scope is removed.
  </Tab>
  <Tab title="Combine materials">
    Combine 2 pieces of wood with 1 nail to create a wooden plank:

    ```lua
        ["wood"] = {
            sourceQuantityRequired = 2,
            sourceIsToRemove = true,               -- Remove the 2 wood pieces
            targetItem = "nail",
            targetQuantity = 1,
            targetIsToRemove = true,               -- Remove the nail
            resultItem = "wooden_plank",
            resultQuantity = 1,
        },
    ```

    **How to use:** Drag 2 wood items over 1 nail → wooden plank is created, both materials are consumed.
  </Tab>
</Tabs>

## Important notes

<CardGroup cols={2}>
  <Card title="Same inventory only" icon="box">
    Crafting only works when both items are in the **same inventory** (you can't drag from player inventory to vehicle inventory)
  </Card>

  <Card title="Item names must match" icon="fingerprint">
    The `targetItem` and `resultItem` names must exactly match the item names in `_data/items.lua`
  </Card>

  <Card title="Quantity checks" icon="calculator">
    The system automatically checks if you have enough items before crafting
  </Card>

  <Card title="Multiple recipes" icon="layer-group">
    You can add as many recipes as you want to the `CRAFTING_RECIPES` table
  </Card>
</CardGroup>

<Warning>
  **One source, multiple targets:** Each source item can only have one recipe. If you need multiple recipes for the same source item, you'll need to use different source items or create separate crafting systems.
</Warning>