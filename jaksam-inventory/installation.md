---
title: "Installation"
icon: "table-rows-add-below"
description: "The installation of the script is extremely easy."
---

## Requirements

- **ESX** (1.10.7, 1.11.3+, or 1.14.0+), **QBCore**, or **QBX**
- `jaksam_core`
- `oxmysql` and `ox_lib` (see the Start Order Example for your framework below)

<Warning>
  **Do NOT use FileZilla** to upload the files, otherwise the script will **NOT** work. Use [WinSCP](https://winscp.net/eng/download.php) instead.
</Warning>

<Tabs>
  <Tab title="ESX 1.10.7">
    1. Download the script and extract it into your resources.
    2. Download `jaksam_core` and extract it into your resources.
    3. Add the following code **right after** `es_extended` in your `server.cfg`:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Allows jaksam's inventory to automatically install itself
    ensure jaksam_inventory
    ```

    4. In `es_extended/config.lua`, set:

    ```lua
    Config.OxInventory = false
    ```

    5. In `es_extended/config.lua`, set:

    ```lua
    Config.EnableDefaultInventory = false
    ```

    6. The script will **automatically** set up the database. If it doesn't, you can manually run the files in the `jaksam_inventory/sql/` folder.

    ### Start Order Example

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## ESX
    ensure es_extended
    ensure jaksam_inventory
    
    # Other ESX scripts
    start [core]
    ```

    <Warning>
      If it doesn't work, be sure to use the latest version of the official ESX with all required dependencies.
    </Warning>
  </Tab>
  <Tab title="ESX 1.11.3+">
    1. Download the script and extract it into your resources.
    2. Download `jaksam_core` and extract it into your resources.
    3. Add the following code **right after** `es_extended` in your `server.cfg`:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Allows jaksam's inventory to automatically install itself
    ensure jaksam_inventory
    ```

    4. In `es_extended/config.lua`, set:

    ```lua
    Config.CustomInventory = "jaksam_inventory"
    ```

    5. The script will **automatically** set up the database. If it doesn't, you can manually run the files in the `jaksam_inventory/sql/` folder.

    ### Start Order Example

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## ESX
    ensure es_extended
    ensure jaksam_inventory
    
    # Other ESX scripts
    start [core]
    ```
  </Tab>
  <Tab title="ESX 1.14.0+">
    1. Download the script and extract it into your resources.
    2. Download `jaksam_core` and extract it into your resources.
    3. Add the following code **right after** `es_extended` in your `server.cfg`:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Allows jaksam's inventory to automatically install itself
    ensure jaksam_inventory
    ```

    4. In `es_extended/shared/config/main.lua`, set:

    ```lua
    Config.CustomInventory = "jaksam_inventory"
    ```

    5. The script will **automatically** set up the database. If it doesn't, you can manually run the files in the `jaksam_inventory/sql/` folder.

    ### Start Order Example

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## ESX
    ensure es_extended
    ensure jaksam_inventory
    
    # Other ESX scripts
    start [core]
    ```
  </Tab>
  <Tab title="QBCore">
    1. Download the script and extract it into your resources.
    2. Download `jaksam_core` and extract it into your resources.
    3. Enable `Integrations.backwardsCompatibility` for `qb-inventory` in `jaksam_inventory/integrations/sv_integrations.lua`.
    4. Add the following code **right after** `qb-core` in your `server.cfg`:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Allows jaksam's inventory to automatically install itself
    ensure jaksam_inventory
    ```

    5. The script will **automatically** set up the database. If it doesn't, you can manually run the files in the `jaksam_inventory/sql/` folder.

    ### Start Order Example

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## QBCore
    ensure qb-core
    ensure jaksam_inventory
    
    # Other QBCore scripts
    ```

    <Warning>
      If it doesn't work, be sure to use the latest version of the official QBCore with all required dependencies.
    </Warning>
  </Tab>
  <Tab title="QBX">
    1. Download the script and extract it into your resources.
    2. Download `jaksam_core` and extract it into your resources.
    3. Enable `Integrations.backwardsCompatibility` for `ox_inventory` in `jaksam_inventory/integrations/sv_integrations.lua`.
    4. Add the following code **right after** `qbx_core` in your `server.cfg`:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Allows jaksam's inventory to automatically install itself
    ensure jaksam_inventory
    ```

    5. The script will **automatically** set up the database. If it doesn't, you can manually run the files in the `jaksam_inventory/sql/` folder.

    ### Start Order Example

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## QBX
    ensure qbx_core
    ensure jaksam_inventory
    
    # Other QBX scripts
    ```

    <Warning>
      If it doesn't work, be sure to use the latest version of the official QBX with all required dependencies.
    </Warning>
  </Tab>
</Tabs>

You are ready to go! Enjoy the script 😁

## Verification

Use the `/inventory` command in-game. If your inventory opens, the script is running correctly.

## Importing Old Items and Inventories

<Tabs>
  <Tab title="ESX">
    1. Go in-game.
    2. Use the `/inventory` command and go to **Settings**.
    3. Click **Import from ESX**.
    4. Done!
  </Tab>
  <Tab title="QBCore">
    1. Only during this process, make sure the **original `qb-inventory`** is running. After the import, you can and should remove it.
    2. Use the `/inventory` command and go to **Settings**.
    3. Click **Import from QBCore**.
    4. Done!
  </Tab>
  <Tab title="OX Inventory">
    1. Only during this process, make sure `ox_inventory` is running. After the import, you can and should remove it.
    2. Use the `/inventory` command and go to **Settings**.
    3. Click **Import from OX inventory**.
    4. Done!
  </Tab>
  <Tab title="qs-inventory">
    1. Only during this process, make sure `qs-inventory` is running. After the import, you can and should remove it.
    2. Use the `/inventory` command and go to **Settings**.
    3. Click **Import from qs-inventory**.
    4. Done!
  </Tab>
  <Tab title="Chezza Inventory">
    1. Only during this process, make sure the **Chezza inventory** is running. After the import, you can and should remove it.
    2. Use the `/inventory` command and go to **Settings**.
    3. Click **Import from Chezza inventory**.
    4. Done!
  </Tab>
  <Tab title="TGiann Inventory">
    1. Only during this process, make sure the **TGiann inventory** is running. After the import, you can and should remove it.
    2. Use the `/inventory` command and go to **Settings**.
    3. Click **Import from TGiann inventory**.
    4. Done!
  </Tab>
</Tabs>

## Backwards Compatibility

This inventory lets you use your old scripts, even if they require a different inventory system.

### Default Framework Functions

You can use the normal inventory functions provided by your framework.

### OX Inventory Compatibility

If your old scripts use **OX Inventory**, you can enable easy compatibility.

1. Go to `jaksam_inventory/integrations/sv_integrations.lua`.
2. Enable `ox_inventory` in `Integrations.backwardsCompatibility`.
3. The server may require a restart after it loads for the first time with these settings.

### QB Inventory Compatibility

If your old scripts use **QB Inventory**, you can enable easy compatibility.

1. Go to `jaksam_inventory/integrations/sv_integrations.lua`.
2. Enable `qb-inventory` in `Integrations.backwardsCompatibility`.
3. The server may require a restart after it loads for the first time with these settings.

That's all! Your old scripts should now work with this inventory.