---
title: "Installation"
description: "Install Jaksam Identity on your FiveM server with ESX, QBCore or Qbox, add the items to your inventory and configure the first offices and workshops."
icon: "download"
---

Get **Jaksam Identity** up and running on your FiveM server.

## Requirements

| Resource | Why |
| --- | --- |
| `es_extended` (with the esx_license tables) **or** `qb-core` / `qbx_core` | Framework |
| `jaksam_inventory` 1.28 or newer, **or** `ox_inventory`, **or** `qb-inventory` 2.2 (QBCore version only) | Documents are items with data |
| `ox_lib`, `oxmysql` | Callbacks, menus, database |
| `ox_target` **or** `qb-target` (QBCore version only) | Targets |
| `bob74_ipl` | The forgery workshop interior |
| RoadPhone (optional) | Phone numbers on business cards, [phone wallet](/jaksam-identity/guides/roadphone-wallet) |
| `esx_dmvschool` (optional, ESX only) | The first driver licence is issued after the driving test |

<Warning>
  The script creates and updates its own database tables on start. **Back up your database** before installing and before every update.
</Warning>

## Install the resource

There is one version for **ESX** and one for **QBCore and Qbox** (it finds out which of the two runs). Take the one for your framework.

<Tabs>
  <Tab title="ESX" icon="server">
    <Steps>
      <Step title="Download Jaksam Identity">
        Download the ESX version and extract the `jksm_identity` folder into your server's `resources` folder.
      </Step>
      <Step title="Configure server.cfg">
        Start it **after** everything it needs, for example:

        ```cfg
        ensure oxmysql
        ensure ox_lib
        ensure es_extended
        ensure jaksam_inventory
        ensure ox_target
        ensure bob74_ipl
        ensure jksm_identity
        ```
      </Step>
      <Step title="Database">
        Nothing to do: the tables are created and updated on start (`jksm_identity_schema` holds the version).

        `install/install.sql` is only for databases where the script is not allowed to create tables.
      </Step>
      <Step title="Add the items">
        Add the items to your inventory, see [Add the items](#add-the-items) below.
      </Step>
      <Step title="config/main.lua">
        - `Config.Bridge`: inventory (`'jaksam'` or `'ox_inventory'`), notifications (`'esx'` or `'ox_lib'`), phone (`'roadphone'` or `'none'`) and menus
        - `Config.Locale`: `'en'` or `'de'`
        - `Config.AdminGroups` / `Config.AdminAce`: who may use the admin command
        - `Config.Debug = false` on a live server
      </Step>
    </Steps>

    <Warning>
      **esx_dmvschool:** its event `esx_dmvschool:addLicense` is not checked on the server, so a cheating client can grant itself any licence with it. Jaksam Identity trusts the licences in the database and, with `Config.DmvSchool` on, issues the driver licence after that event. Secure the event in esx_dmvschool, or set `Config.DmvSchool.enabled = false`, on a live server.
    </Warning>
  </Tab>
  <Tab title="QBCore / Qbox" icon="server">
    <Steps>
      <Step title="Download Jaksam Identity">
        Download the QBCore version and extract the `jksm_identity` folder into your server's `resources` folder.
      </Step>
      <Step title="Remove qbx_idcard (Qbox)">
        Jaksam Identity takes its place: it answers to the name `qbx_idcard`, its exports `GetMetaLicense` and `CreateMetaLicense` and its show event, so qbx_core's starter items and qbx_cityhall keep working unchanged.

        <Warning>
          With `qbx_idcard` still running, two cards would open.
        </Warning>
      </Step>
      <Step title="Configure server.cfg">
        Start it **after** everything it needs, for example:

        ```cfg
        ensure oxmysql
        ensure ox_lib
        ensure qb-core
        ensure qb-inventory
        ensure qb-target
        ensure bob74_ipl
        ensure jksm_identity
        ```
      </Step>
      <Step title="Database">
        Nothing to do: the tables are created and updated on start (`jksm_identity_schema` holds the version).

        `install/install.sql` is only for databases where the script is not allowed to create tables.
      </Step>
      <Step title="Add the items">
        Add the items to your inventory, see [Add the items](#add-the-items) below.
      </Step>
      <Step title="config/main.lua">
        - `Config.Bridge.framework = 'auto'` finds out whether qb-core or qbx_core runs
        - `Config.Bridge.target = 'auto'` uses ox_target when it is installed, else qb-target
        - `Config.Bridge.inventory`: `'jaksam'`, `'ox_inventory'` or `'qb-inventory'`
        - `Config.Locale`: `'en'` or `'de'`
        - `Config.AdminGroups` / `Config.AdminAce`: who may use the admin command
        - `Config.Debug = false` on a live server
      </Step>
    </Steps>

    <Info>
      - **Items:** the ID card, driver licence and firearms permit are QBCore's own items `id_card`, `driver_license` and `weaponlicense`. Badges, business cards and the workshop material are this script's items.
      - **Starter items and city hall:** what qb-core, qbx_core and qb-cityhall / qbx_cityhall hand out becomes a registered document of the character. qbx_cityhall issues it with a photo taken there.
      - **Old card fields:** every card also carries `citizenid`, `birthdate`, `nationality` and `cardtype` for scripts that read them.
      - **Licences** come from the character metadata `licences` (`driver` is the script's `drive`).
      - **Black money:** on QBCore the `markedbills` item (its value in `metadata.worth`), on Qbox the stackable `black_money` item.
      - esx_dmvschool support is in the ESX version only.
    </Info>
  </Tab>
</Tabs>

## Add the items

<Tabs>
  <Tab title="jaksam_inventory" icon="boxes-stacked">
    <Steps>
      <Step title="Add the item entries">
        Add the entries of `install/jaksam_items.lua` to `jaksam_inventory_data/items.lua`, inside the table after `return { }`.
      </Step>
      <Step title="Add the item types">
        Copy `install/jaksam_item_types.lua` as it is to `jaksam_inventory_data/_data/jksm_identity.lua`. It adds the right-click actions **View**, **Show** and **Copy number**. Nothing to paste: files in that folder survive inventory updates.
      </Step>
      <Step title="Copy the images">
        Copy `install/images/*.webp` to `jaksam_inventory_data/_images/`.
      </Step>
      <Step title="Restart the inventory">
        Restart `jaksam_inventory` once.
      </Step>
    </Steps>

    See [Items from shops or admin gives](#items-from-shops-or-admin-gives) for the metadata block every document item must keep.
  </Tab>
  <Tab title="ox_inventory" icon="box">
    Set `Config.Bridge.inventory = 'ox_inventory'` and `Config.InventoryKeys = { 'TAB' }` (the key that opens the inventory next to an open card).

    <Steps>
      <Step title="Add the items">
        Add `install/ox_items.lua` to `ox_inventory/data/items.lua`.
      </Step>
      <Step title="Copy the images">
        Copy `install/images/*.webp` to `ox_inventory/web/images/`.
      </Step>
    </Steps>

    - The documents get a use export (show or look, `Config.UseAction`) and the right-click buttons **View** and **Show**. Copying the number is ox_inventory's own "Copy serial number".
    - **Shop and admin-given documents** get their data from the script through ox's `createItem` hook, no metadata needed in the item definitions.
    - **ID stacks** are ox containers, set up by the script. A wallet only counts for the phone wallet if it is an ox container (`setContainerProperties`) listed in `Config.WalletContainers`. ox does not allow a container inside another container.
    - **Documents on the ground** can be viewed by whoever opened that drop.
  </Tab>
  <Tab title="qb-inventory" icon="box-open">
    QBCore version only, built for **qb-inventory 2.2**. Set `Config.Bridge.inventory = 'qb-inventory'` and `Config.InventoryKeys = { 'TAB' }`.

    <Steps>
      <Step title="Add the items">
        Add `install/qb_items.lua` to `qb-core/shared/items.lua`, replacing the three card items QBCore already has.
      </Step>
      <Step title="Copy the images">
        Copy `install/images/*.webp` to `qb-inventory/html/images/`.
      </Step>
    </Steps>

    Nothing inside qb-inventory has to be changed, and its own chat ID card no longer shows.

    - **Using a document** shows or opens it (`Config.UseAction`). qb-inventory has no right-click buttons, so set `Config.UseAction = 'menu'` to pick between looking and showing each time. A business card always asks (look, show, hand over). The number is copied from the open card.
    - **Documents from starter items, the city hall, a shop or `/giveitem`** get their data from the script (qb-inventory's `ItemAdded` hook).
    - **No ID stacks:** qb-inventory has no containers. The documents of an order arrive one by one in the results storage, and the phone wallet reads the main inventory only.
    - **A storage is open for one player at a time** (qb-inventory's rule). What the workers put in while it is open shows after opening it again.

    <Warning>
      **Sealed documents:** qb-inventory takes an item's data from the client when a player gives or drops it. Every document therefore carries a seal made with a key only the server knows (table `jksm_identity_settings`, made on the first start). A document whose data was made up or changed has no valid seal: it shows nothing and says so. **Keep that table when you move the database**, or the documents in the inventories lose their seal.
    </Warning>
  </Tab>
</Tabs>

### Items from shops or admin gives

When the script issues a document it passes the metadata itself. When a document item comes into existence another way (a jaksam shop, an admin give), the metadata templates fill it. The entries in `install/jaksam_items.lua` already carry this block, keep it on every document item:

```lua
dynamicMetadata = {
    serial    = { metadataTemplateId = 'doc_serial',    onlyFirstAdd = true },
    firstname = { metadataTemplateId = 'doc_firstname', onlyFirstAdd = true },
    lastname  = { metadataTemplateId = 'doc_lastname',  onlyFirstAdd = true },
    dob       = { metadataTemplateId = 'doc_dob',       onlyFirstAdd = true },
    sex       = { metadataTemplateId = 'doc_sex',       onlyFirstAdd = true },
    issued    = { metadataTemplateId = 'doc_issued',    onlyFirstAdd = true },
    expires   = { metadataTemplateId = 'doc_expires',   onlyFirstAdd = true },
    classes   = { metadataTemplateId = 'doc_classes',   onlyFirstAdd = true }, -- only with licence classes
},
```

The templates are registered on start and again whenever jaksam_inventory restarts. A template-made document is **registered** (real), unless its jaksam `rarity` is listed in `Config.UnregisteredRarities` (default `illegal`).

## Configure

<Steps>
  <Step title="config/documents.lua">
    The document types, their items, validity and themes. Any licence your framework knows can become a document: add the item and one entry here. See [Documents and register](/jaksam-identity/guides/documents-and-register).
  </Step>
  <Step title="config/office.lua">
    The starter documents (`Config.Starter`, by default the ID card) and the citizen offices (`Config.Offices`): places, NPC models, which documents each office handles, fees, cash or bank. See [Citizen offices](/jaksam-identity/guides/citizen-offices).
  </Step>
  <Step title="config/forgery.lua">
    List the forgery workshops in `Config.Forgery.workshops` (entrance outside, price, the jobs that may own it), or add them in game with `/documents config`. **No workshop is configured out of the box**: the forgery side stays invisible until you add one. See [Forgery workshops](/jaksam-identity/guides/forgery-workshops).
  </Step>
  <Step title="config/raid.lua">
    The forces that raid workshops (your police jobs, from which rank) and where the evidence locker of each force stands. Without a locker nothing can be seized. `Config.Raid.enabled = false` turns raids off. See [Raids](/jaksam-identity/guides/raids).
  </Step>
</Steps>

<Tip>
  Most of these settings, places included, can be changed in game with `/documents config`, without editing files or restarting. See [Settings in game](/jaksam-identity/guides/settings-in-game).
</Tip>

## Verification

Start the server and read the console. A missing resource or a bridge without a file is named in red. **No red line means the start checks passed** (with `Config.Debug = true` it also prints `start checks passed`).

In game, open `/documents` as an admin: without a subcommand it lists all the available ones.
