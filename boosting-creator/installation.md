---
title: "Installation"
description: "Install Boosting Creator on your FiveM server with ESX, QBCore or Qbox, add the laptop item and give the admin permission."
icon: "download"
---

Get **Boosting Creator** up and running on your FiveM server.

## Requirements

| Resource | Why |
| --- | --- |
| `es_extended` **or** `qb-core` / `qbx_core` | Framework |
| `ox_lib` | Callbacks and optional modules |
| `oxmysql` (or `mysql-async`) | Database |
| OneSync | Contract cars, guards and chasers are networked entities |
| `vehicles_keys` (optional) | Lockpick and hotwire with vehicles_keys, temporary keys for the stolen car |
| `datacrack`, `utk_fingerprint`, `ultra-keypackhack` (optional) | Extra hack minigames |

<Warning>
  Contract cars, guards, garage cars, the car carrier and the chasing crew are created by the thief's game and checked by the server. With `sv_entityLockdown strict` nothing can spawn and every contract is cancelled right after it starts.
</Warning>

<Danger>
  Do **NOT** use FileZilla to upload the files, otherwise the script will **NOT** work.

  Use [WinSCP](https://winscp.net/eng/download.php) instead.
</Danger>

## Install the resource

There is one version for **ESX** and one for **QBCore and Qbox**. Take the one for your framework.

<Steps>
  <Step title="Download Boosting Creator">
    Download the version for your framework and extract the `boosting_creator` folder into your server's `resources` folder.
  </Step>
  <Step title="Configure server.cfg">
    Start it **after** everything it needs, for example:

    ```cfg
    ensure oxmysql
    ensure ox_lib
    ensure es_extended
    ensure vehicles_keys
    ensure boosting_creator
    ```
  </Step>
  <Step title="Database">
    Nothing to do: the tables are created on the first start and new columns are added by every update.

    The files in `boosting_creator/sql/` are only for databases where the script is not allowed to create tables.
  </Step>
  <Step title="Add the laptop item">
    Players open the boosting laptop with an item, `boosting_laptop` by default. See [Add the laptop item](#add-the-laptop-item) below.
  </Step>
  <Step title="Give the admin permission">
    See [Admin permission](#admin-permission) below, then open the panel with `/boostingcreator`.
  </Step>
</Steps>

## Add the laptop item

The item name is set in the panel, **Settings > General > Laptop item**. Changing it needs a script restart.

<Tabs>
  <Tab title="jaksam inventory">
    Nothing to do: the item is created automatically on start, and again when the inventory restarts.

    For the item picture, copy `boosting_creator/images/boosting_laptop.png` to `jaksam_inventory_data/_images/`.
  </Tab>
  <Tab title="ox_inventory">
    Add this to `ox_inventory/data/items.lua`:

    ```lua
    ['boosting_laptop'] = {
        label = 'Boosting Laptop',
        weight = 1000,
        stack = false,
        close = true,
        description = 'Contracts for those who know where to look',
    },
    ```

    The script listens to ox_inventory's own use event, no `server.export` needed.

    For the item picture, copy `boosting_creator/images/boosting_laptop.png` to `ox_inventory/web/images/`.
  </Tab>
  <Tab title="ESX">
    Run this on your database:

    ```sql
    INSERT IGNORE INTO `items` (`name`, `label`, `weight`) VALUES ('boosting_laptop', 'Boosting Laptop', 1);
    ```
  </Tab>
  <Tab title="QBCore">
    Add this to `qb-core/shared/items.lua`:

    ```lua
    ['boosting_laptop'] = {['name'] = 'boosting_laptop', ['label'] = 'Boosting Laptop', ['weight'] = 1000, ['type'] = 'item', ['image'] = 'boosting_laptop.png', ['unique'] = true, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Contracts for those who know where to look'},
    ```

    For the item picture, copy `boosting_creator/images/boosting_laptop.png` to `qb-inventory/html/images/`.
  </Tab>
</Tabs>

<Info>
  If the item doesn't exist, the server console says so at start in yellow: `The item boosting_laptop doesn't exist, create it in your inventory to use the laptop`.
</Info>

## Admin permission

The panel and every admin action check an ace, `boostingcreator` by default (changeable in **Settings > General**). The ace `jaksam` always works too.

```cfg
add_ace group.admin boostingcreator allow
```

<Tip>
  Without the permission, `/boostingcreator` opens a window with the exact `add_ace` lines for your own license and Steam account, ready to copy into `server.cfg`.
</Tip>

## Verification

Open `/boostingcreator` (or `/boostcreator`) in game. If the panel opens with the classes D to S already there, the script is running correctly.

Then give yourself the laptop, use it and join the queue: the first offer comes after 45 to 120 seconds with the default settings.

## Updating

<Warning>
  Before updating, back up `boosting_creator/current_config.json` (every setting of the panel) and the `boosting_creator/integrations/` folder, then put them back in the new version. Replacing the folder without them brings back the default settings and the default integrations.
</Warning>

Classes, vehicles, locations, fixers and player profiles are in the database and are kept. See also [How to update the scripts](/jaksams-scripts/how-to-update-the-scripts).
