---
title: "Installation"
description: "Install Vehicles Keys on your FiveM server with ESX or QBCore, including optional default items setup."
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
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `vehicles_keys/sql/` folder.
      </Step>
      <Step title="Lockpicking script">
        Download and start the [lockpicking script](https://github.com/baguscodestudio/lockpick) _(credits to [baguscodestudio](https://github.com/baguscodestudio/lockpick))_.
      </Step>
    </Steps>

    ### Adding the items — Optional

    To add the premade items, you only have to run the file `vehicles_keys/sql/items_limit.sql` **or** `vehicles_keys/sql/items_weight.sql`, depending on whether your server uses limit or weight.

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
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `vehicles_keys/sql/` folder.
      </Step>
      <Step title="Lockpicking script">
        Download and start the [lockpicking script](https://github.com/baguscodestudio/lockpick) _(credits to [baguscodestudio](https://github.com/baguscodestudio/lockpick))_.
      </Step>
      <Step title="Install menu_default">
        Download and extract the [menu_default](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) script in your resources, **without renaming it**, and add it to your auto start (example: `server.cfg`).
      </Step>
    </Steps>

    ### Adding the items — Optional

    To add the new items, edit the `qb-core/shared/items.lua` file and add the following code at the bottom of the table:

    ```lua
    -- Vehicles Keys items
    ['vehicle_alarm_1'] = {['name'] = 'vehicle_alarm_1', ['label'] = 'Vehicle alarm level 1', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Vehicle alarm level 1'},
    ['vehicle_alarm_2'] = {['name'] = 'vehicle_alarm_2', ['label'] = 'Vehicle alarm level 2', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Vehicle alarm level 2'},
    ['vehicle_alarm_3'] = {['name'] = 'vehicle_alarm_3', ['label'] = 'Vehicle alarm level 3', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Vehicle alarm level 3'},
    ['vehicle_alarm_4'] = {['name'] = 'vehicle_alarm_4', ['label'] = 'Vehicle alarm level 4', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Vehicle alarm level 4'},
    ['vehicle_transfer_contract'] = {['name'] = 'vehicle_transfer_contract', ['label'] = 'Vehicle transfer contract', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Used to sell your vehicle to someone'},
    ```

    <Frame caption="Example screenshot">
      ![QBCore Vehicles Keys items example](/images/qb_core_vehicles_keys_items.png)
    </Frame>
  </Tab>
</Tabs>

You are ready to go! Enjoy the script 😁

## Optional step

After the database is set up correctly, you can delete the files in `vehicles_keys/sql/` folder, so the script won't try to set up the database each time you start it.
