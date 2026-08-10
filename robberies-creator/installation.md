---
title: "Installation"
description: "Install Robberies Creator on your FiveM server with ESX, QBCore, or OX Inventory, including optional minigame scripts and default items setup."
icon: "download"
---

The installation of the script is extremely easy.

<Danger>
  Do **NOT** use FileZilla to upload the files, otherwise the script will **NOT** work.

  Use [WinSCP](https://winscp.net/eng/download.php) instead.
</Danger>

<Tabs>
  <Tab title="ESX">
    <Steps>
      <Step title="Download and extract">
        Download the script and extract it in your resources.
      </Step>
      <Step title="Add to auto start">
        Add the script in your auto start (example: `server.cfg`).
      </Step>
      <Step title="Database setup">
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `robberies_creator/sql/` folder.
      </Step>
      <Step title="Cracking safe script">
        Download and start the [cracking safe script](https://github.com/VHall1/pd-safe) _(credits to [VHall1](https://github.com/VHall1))_.
      </Step>
      <Step title="Lockpicking script">
        Download and start the [lockpicking script](https://github.com/baguscodestudio/lockpick) _(credits to [baguscodestudio](https://github.com/baguscodestudio/lockpick))_.
      </Step>
      <Step title="Optional minigame scripts">
        - Download and start the [datacrack minigame script](https://github.com/utkuali/datacrack) _(credits to [utkuali](https://github.com/utkuali))_
        - Download and start the [fingerprint minigame script](https://github.com/utkuali/Finger-Print-Hacking-Game) _(credits to [utkuali](https://github.com/utkuali))_
        - Download and start the [memory minigame script](https://github.com/ultrahacx/ultra-keypackhack) _(credits to [ultrahacx](https://github.com/ultrahacx))_
      </Step>
    </Steps>

    ### Adding the items — Optional

    To add the premade items, you only have to run the file `robberies_creator/sql/items_limit.sql` **or** `robberies_creator/sql/items_weight.sql`, depending on whether your server uses limit or weight.

    <Info>
      The latest version of ESX uses **weight**.
    </Info>

    <Danger>
      If it doesn't work, be sure to use the latest official version of ESX with the required dependencies.
    </Danger>
  </Tab>
  <Tab title="QBCore">
    <Steps>
      <Step title="Download and extract">
        Download the script and extract it in your resources.
      </Step>
      <Step title="Add to auto start">
        Add the script in your auto start (example: `server.cfg`).
      </Step>
      <Step title="Database setup">
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `robberies_creator/sql/` folder.
      </Step>
      <Step title="Cracking safe script">
        Download and start the [cracking safe script](https://github.com/VHall1/pd-safe) _(credits to [VHall1](https://github.com/VHall1))_.
      </Step>
      <Step title="Lockpicking script">
        Download and start the [lockpicking script](https://github.com/baguscodestudio/lockpick) _(credits to [baguscodestudio](https://github.com/baguscodestudio/lockpick))_.
      </Step>
      <Step title="Optional minigame scripts">
        - Download and start the [datacrack minigame script](https://github.com/utkuali/datacrack) _(credits to [utkuali](https://github.com/utkuali))_
        - Download and start the [fingerprint minigame script](https://github.com/utkuali/Finger-Print-Hacking-Game) _(credits to [utkuali](https://github.com/utkuali))_
        - Download and start the [memory minigame script](https://github.com/ultrahacx/ultra-keypackhack) _(credits to [ultrahacx](https://github.com/ultrahacx))_
      </Step>
    </Steps>

    ### Adding the items — Optional

    To add the new items, edit the `qb-core/shared/items.lua` file and add the following code at the bottom of the table:

    ```lua
    -- Robberies Creator items
    ['hacking_computer'] = {['name'] = 'hacking_computer', ['label'] = 'Hacking computer', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Computer to hack panels'},
    ['thermal_charge'] = {['name'] = 'thermal_charge', ['label'] = 'Thermal charge', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Use to melt some doors'},
    ['gas_mask'] = {['name'] = 'gas_mask', ['label'] = 'Gas mask', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Protects from lethal gas'},
    ['drill'] = {['name'] = 'drill', ['label'] = 'Drill', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Can be used to open trucks doors'},
    ['gold_ingot'] = {['name'] = 'gold_ingot', ['label'] = 'Gold ingot', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Goooold'},
    ['diamonds_box'] = {['name'] = 'diamonds_box', ['label'] = 'Diamond box', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Diamooonds'},
    ['lockpick'] = {['name'] = 'lockpick', ['label'] = 'Lockpick', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Used to lockpick doors'},
    ['painting'] = {['name'] = 'painting', ['label'] = 'Painting', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Expensive painting'},
    ```

    <Frame caption="Example screenshot">
      ![QBCore Robberies Creator items example](/images/qb_core_robberies_creator_items.png)
    </Frame>
  </Tab>
  <Tab title="OX Inventory">
    Here's a list of items to use with OX Inventory. You can even use it with jaksam's inventory, in the "import from code" setting.

    ```lua
    ['hacking_computer'] = {
        label = 'Hacking computer',
        weight = 500,
        stack = true,
        close = true,
        description = 'Computer to hack panels'
    },

    ['thermal_charge'] = {
        label = 'Thermal charge',
        weight = 500,
        stack = true,
        close = true,
        description = 'Use to melt some doors'
    },

    ['gas_mask'] = {
        label = 'Gas mask',
        weight = 500,
        stack = true,
        close = true,
        description = 'Protects from lethal gas'
    },

    ['drill'] = {
        label = 'Drill',
        weight = 500,
        stack = true,
        close = true,
        description = 'Can be used to open trucks doors'
    },

    ['gold_ingot'] = {
        label = 'Gold ingot',
        weight = 500,
        stack = true,
        close = true,
        description = 'Goooold'
    },

    ['diamonds_box'] = {
        label = 'Diamond box',
        weight = 500,
        stack = true,
        close = true,
        description = 'Diamooonds'
    },

    ['lockpick'] = {
        label = 'Lockpick',
        weight = 500,
        stack = true,
        close = true,
        description = 'Used to lockpick doors'
    },

    ['painting'] = {
        label = 'Painting',
        weight = 500,
        stack = true,
        close = true,
        description = 'Expensive painting'
    },
    ```
  </Tab>
</Tabs>

You are ready to go! Enjoy the script 😁

## Optional step

After the database is set up correctly, you can delete the files in `robberies_creator/sql/` folder, so the script won't try to set up the database each time you start it.
