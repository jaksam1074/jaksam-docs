---
title: "Weapon Attachments"
icon: "gun"
description: "Map multiple weapon component IDs to a single attachment item"
---

## Why this guide exists

In GTA V, each weapon has different component IDs for the same attachment type. For example:

- A suppressor for a Pistol uses `COMPONENT_AT_PI_SUPP`
- A suppressor for a Combat Pistol uses `COMPONENT_AT_PI_SUPP_02`

**The inventory system simplifies this:** You can create ONE item (like "suppressor") that automatically works with all compatible weapons by mapping multiple component IDs to it.

## Step-by-step guide

### Step 1: Check if the item exists

First, check if an item for your attachment type already exists in your database.

<Tabs>
  <Tab title="Vanilla GTA weapons">
    - Most common attachments (suppressor, extended clip, flashlight, etc.) should already exist
    - Use `/inventory` command in-game to check existing items
  </Tab>
  <Tab title="Modded weapons">
    - You'll need to create a new item OR add the modded weapon's component hash to an existing item
    - Example: If you have a modded AK47 with a suppressor, you can add its suppressor hash to the existing "suppressor" item
  </Tab>
</Tabs>

**Creating/Editing the item:**

<Steps>
  <Step title="Open the inventory management UI">
    Type `/inventory` in-game.
  </Step>
  <Step title="Create or edit an item">
    Create a new item or edit an existing one.
  </Step>
  <Step title="Set the correct item type">
    <CardGroup cols={2}>
      <Card title="barrel">
        Suppressors, muzzle brakes
      </Card>

      <Card title="clip">
        Magazines
      </Card>

      <Card title="scope">
        Sights and optics
      </Card>

      <Card title="flashlight">
        Tactical lights
      </Card>

      <Card title="grip">
        Foregrips
      </Card>
    </CardGroup>

    <Frame caption="Example with default suppressor">
      ![Edit default suppressor item component example](/images/weapon-attachments-item-example.png)
    </Frame>
  </Step>
</Steps>

### Step 2: Add component hashes

Now you need to add the component hash(es) that this item should apply to weapons.

**Where to find component hashes:**

<Tabs>
  <Tab title="Vanilla GTA weapons">
    - Check the [wiki](https://docs.fivem.net/docs/game-references/weapon-models/)
    - Or search online for "GTA V weapon components list"
  </Tab>
  <Tab title="Modded weapons">
    - Most likely your modded weapon script contains a text file, with the component hashes
    - An example for component names, may be that they start with `COMPONENT_`
    - Contact the weapon's creator/documentation if you can't find it
  </Tab>
</Tabs>

**How to add them:**

<Steps>
  <Step title="Open the Component Hashes section">
    In the item edit screen for the attachment item, find the "Component Hashes" section.
  </Step>
  <Step title="Add a hash">
    Click "Add Component Hash".
  </Step>
  <Step title="Enter the hash">
    Enter the component hash (e.g., `COMPONENT_AT_PI_SUPP`).
  </Step>
  <Step title="Repeat">
    Repeat for all components you want this attachment to work with.
  </Step>
</Steps>

<Info>
  The menu will show you what weapons are compatible with each component hash you add.
</Info>

<Frame caption="Edit item hashes list example">
  ![Edit item hashes list example](/images/weapon-attachments-hashes-example.png)
</Frame>

### Step 3: Test in-game

<Steps>
  <Step title="Give yourself the item">
    `/giveitem [your_id] [item_name] 1` or through omnipack (`F1` while inventory is open).
  </Step>
  <Step title="Give yourself a weapon">
    Give yourself a compatible weapon.
  </Step>
  <Step title="Attach it">
    Try to attach the component.
  </Step>
</Steps>

<Tip>
  That's it! The system will automatically apply the correct component based on the weapon.
</Tip>

## Complete Example

Let's say you want to add a suppressor for a modded weapon called "WEAPON\_MODDEDAK47":

<Steps>
  <Step title="Check existing items">
    Open `/inventory` and search for "suppressor" - it exists!
  </Step>
  <Step title="Edit the item">
    Click edit on the suppressor item.
  </Step>
  <Step title="Add the hash">
    Add `COMPONENT_MODDEDAK47_SUPP` to the component hashes list.
  </Step>
  <Step title="Save">
    Save the item.
  </Step>
  <Step title="Test">
    Give yourself the suppressor and the modded AK47, then try attaching it.
  </Step>
</Steps>