---
title: "Installation"
description: "Install Trackers Creator on your FiveM server with ESX or QBCore, including optional default items setup."
icon: "download"
---

The installation of the script is extremely easy.

## Requirements

- **ESX** or **QBCore**

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
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `trackers_creator/sql/` folder.
      </Step>
    </Steps>

    ### Adding the items — Optional

    To add the premade items, you only have to run the file `trackers_creator/sql/items_limit.sql` **or** `trackers_creator/sql/items_weight.sql`, depending on whether your server uses limit or weight.

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
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `trackers_creator/sql/` folder.
      </Step>
    </Steps>

    ### Adding the items — Optional

    To add the new items, edit the `qb-core/shared/items.lua` file and add the following code at the bottom of the table:

    ```lua
    ['tracker_sender'] = {['name'] = 'tracker_sender', ['label'] = 'Tracker sender', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = false, ['shouldClose'] = false, ['combinable'] = nil},
    ['tracker_receiver'] = {['name'] = 'tracker_receiver', ['label'] = 'Tracker receiver', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = false, ['shouldClose'] = false, ['combinable'] = nil},
    ['private_tracker'] = {['name'] = 'private_tracker', ['label'] = 'Private tracker', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil},
    ```
  </Tab>
</Tabs>

You are ready to go! Enjoy the script 😁

## Verification

<Info>
  [TODO: INFORMATION NEEDED] No in-game check for a successful install is documented yet for Trackers Creator.
</Info>

## Optional step

After the database is set up correctly, you can delete the files in `trackers_creator/sql/` folder, so the script won't try to set up the database each time you start it.
