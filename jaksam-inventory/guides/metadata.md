---
title: "Metadata"
icon: "tags"
description: "Display item metadata to players and set default or dynamic metadata values"
---

## How to show metadata to players

Showing specific metadata to players is easy. First of all, you'll need to know what the metadata key is that you want to show. To do so, you can enable "Debug mode" in the `/inventory` settings menu, then hover the item you want to see the metadata of.

<Columns cols={2}>
  <Frame>
    ![Item debug settings screenshot](/images/metadata-debug-settings.png)
  </Frame>

  <Frame>
    ![Item debug metadata screenshot](/images/metadata-debug-item.png)
  </Frame>
</Columns>

### Adding it to a single item

To show players the metadata of a single item, you can add and adapt this code in the single item definition, in the `jaksam_inventory/_data/items.lua` file:

```lua
displayFields = {
    { field = 'YOUR_METADATA_KEY_HERE', label = 'TEXT YOU WANT HERE: ${value}'}, -- Random example
    { field = 'ammo', label = 'Ammo: ${value}'}, -- Useful on weapons (already built in by default)
    { field = 'plate', label = 'Plate: ${value}'}, -- Useful on carkeys
},
```

<Frame>
  ![Single item display fields example](/images/metadata-single-item-example.png)
</Frame>

### Adding it to all item types

To show players the metadata of an entire item type, it's 100% the same method, but place it in the `Script.defaultsByType` table, in the `jaksam_inventory/_data/defaults.lua` file.

### Optional: Making metadata values look nicer

Sometimes you want to show metadata in a prettier way to players. For example, instead of showing "weapon\_pistol", you want to show "Pistol". This is where formatters come in!

<Tip>
  A formatter is like a translator: it takes the original value (e.g. `weapon_pistol`) and converts it to something nicer (e.g. `Pistol`).
</Tip>

You can use built-in formatters or create your own custom ones in `jaksam_inventory/_data/formatter.lua`. Here's how to use them:

```lua
displayFields = {
    { field = 'item', label = 'Label: ${value}', formatterId = "itemNameToLabel"}, -- An example with built in formatter
},
```

## How to set default metadata for items

Want items to have certain metadata values when they're first created? For example, maybe you want new weapons to start with 50% durability. Here's how to do it:

<Steps>
  <Step title="Open the admin menu">
    Type `/inventory` in-game to open the admin menu.
  </Step>
  <Step title="Find the item">
    Find and click on the item you want to edit.
  </Step>
  <Step title="Open the metadata tab">
    Click on the "metadata" tab.
  </Step>
  <Step title="Set values">
    Set the metadata values you want.
  </Step>
</Steps>

### Advanced - Using templates for dynamic metadata

Sometimes you want metadata that changes based on certain conditions. For this, you can use templates:

<Steps>
  <Step title="Open the metadata tab">
    Go to the same metadata tab in the item editor.
  </Step>
  <Step title="Switch to template type">
    Change the metadata type to `template`.
  </Step>
  <Step title="Choose or create a template">
    Either select an existing template, or create your own in `jaksam_inventory/_data/metadata_templates.lua`.
  </Step>
</Steps>

Templates let you create metadata that updates automatically based on rules you define!

#### Example

Some examples of what you can do with dynamic metadata templates:

- Assign a player's Identification Card their name, birth date, height, etc.
- Assign a random durability to a weapon
- Assign the creation date to an item (the first time the item is created)