---
title: "Installation"
description: "Install Jobs Creator on your FiveM server with ESX or QBCore. Follow the framework-specific setup guide and configure the required database and items."
icon: "download"
---

Get **Jobs Creator** up and running on your FiveM server in just a few steps.

Choose your framework below to view the correct installation instructions.

<Tabs>
  <Tab title="ESX" icon="server">
    <Steps>
      <Step title="Download Jobs Creator">
        Download **Jobs Creator** and extract it into your server's `resources` folder.
      </Step>
      <Step title="Configure server.cfg">
        Add the following to your `server.cfg`:

        ```cfg
        add_unsafe_worker_permission jobs_creator # Allows jobs_creator to automatically install itself
        ensure jobs_creator
        ```
      </Step>
      <Step title="Set up the database">
        Jobs Creator will **automatically set up the database** when the resource starts.

        If the automatic setup fails, you can manually execute the SQL files located in:

        ```text
        jobs_creator/sql/
        ```
      </Step>
      <Step title="Add the included items">
        <Note>
          Adding the included items is **optional**. Choose the SQL file that matches your ESX inventory system.
        </Note>

        **Weight-based inventory**

        Run:

        ```text
        jobs_creator/sql/items_weight.sql
        ```

        **Limit-based inventory**

        Run:

        ```text
        jobs_creator/sql/items_limit.sql
        ```
      </Step>
    </Steps>
  </Tab>
  <Tab title="QBCore" icon="server">
    <Steps>
      <Step title="Download Jobs Creator">
        Download **Jobs Creator** and extract it into your server's `resources` folder.
      </Step>
      <Step title="Configure server.cfg">
        Add the following to your `server.cfg`:

        ```cfg
        add_unsafe_worker_permission jobs_creator # Allows jobs_creator to automatically install itself
        ensure jobs_creator
        ```
      </Step>
      <Step title="Set up the database">
        Jobs Creator will **automatically set up the database** when the resource starts.

        If the automatic setup fails, you can manually execute the SQL files located in:

        ```text
        jobs_creator/sql/
        ```
      </Step>
      <Step title="Install menu_default">
        Download [`menu_default`](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) and extract it into your server's `resources` folder.

        Then add `menu_default` to your `server.cfg`:

        ```cfg
        ensure menu_default
        ```
      </Step>
      <Step title="Add the included items">
        <Note>
          Adding the included items is **optional**.
        </Note>

        Open:

        ```text
        qb-core/shared/items.lua
        ```

        Add the following items to the bottom of the items table:

        ```lua
        ['fixkit'] = {
            ['name'] = 'fixkit',
            ['label'] = 'Fixkit',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['medikit'] = {
            ['name'] = 'medikit',
            ['label'] = 'Medikit',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['sponge'] = {
            ['name'] = 'sponge',
            ['label'] = 'Sponge',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['handcuffs'] = {
            ['name'] = 'handcuffs',
            ['label'] = 'Handcuffs',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['lockpick'] = {
            ['name'] = 'lockpick',
            ['label'] = 'Lockpick',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['bandage'] = {
            ['name'] = 'bandage',
            ['label'] = 'Bandage',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        ```
      </Step>
    </Steps>
  </Tab>
</Tabs>

## Clean Up the SQL Files

<Note>
  Once the database has been successfully configured, you can optionally remove the SQL files from `jobs_creator/sql/`.
</Note>

The SQL files are only required for manual database setup or when adding the included ESX items.