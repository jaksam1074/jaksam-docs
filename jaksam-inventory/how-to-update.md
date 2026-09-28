---
title: "How to"
icon: "rectangle-new"
tag: "Update"
description: "Keep your Jaksam Inventory installation up to date without losing your custom items, settings, integrations, or other customizations."
---

# Updating Jaksam Inventory

Since version **1.28**, updating is much simpler: everything you change lives in its own folder, so an update is just replacing one folder. Pick the guide that matches the version you have installed now:

<CardGroup cols={3}>
  <Card title="1.28 and newer" icon="bolt">
    Replace one folder, nothing to back up or restore
  </Card>

  <Card title="From 1.27 or older to 1.28" icon="right-left">
    Once only: your customizations are moved automatically
  </Card>

  <Card title="Versions before 1.28" icon="clock-rotate-left">
    The old guide, for installations still on 1.27 or older
  </Card>
</CardGroup>

<Tip>
  You can see your installed version in `jaksam_inventory/fxmanifest.lua`, on the `version` line
</Tip>

## Version 1.28 and newer

Everything you change (settings, items, images, hooks, modules, translations, integrations) is saved in **`jaksam_inventory_data`**, a folder next to `jaksam_inventory`. Updates only replace `jaksam_inventory`, so your changes are never touched

<Steps>
  <Step title="Stop your server">
    Stop your FiveM server before replacing the files.
  </Step>
  <Step title="Replace jaksam_inventory">
    Delete the `jaksam_inventory` folder and put the new one in its place. Leave `jaksam_inventory_data` exactly where it is
  </Step>
  <Step title="Start your server">
    That's it: your items, settings and customizations are all still there
  </Step>
</Steps>

<Tip>
  Backing up `jaksam_inventory_data` from time to time is still a good idea: it's the one folder that holds all your work.
</Tip>

<Warning>
  **Don't edit files inside `jaksam_inventory`**, they are replaced by every update. If you do, the server console tells you at startup which file was edited and where that change belongs in `jaksam_inventory_data`. The shipped versions of every file are in `jaksam_inventory/defaults`: read them, copy what you need, but don't edit them.
</Warning>

### What's inside jaksam_inventory_data

| File / Folder | What it holds |
| --- | --- |
| `current_config.json` | Settings from the `/inventory` menu |
| `items.lua` | Your new items, and only the fields you changed of the default ones. The admin menu writes here too |
| `_images/` | Your item images, named like the item (`bread.png`, `bread.webp`) |
| `variables.css` | Default inventory colors. Set it from the theme menu, or paste the output of the `admintheme` F8 command |
| `locales/` | Only the texts you changed |
| `integrations/` | Only the integration functions you changed |
| `_hooks/` | Your hooks. A file with the same name as a default hook replaces it |
| `_modules/` | Your modules. The same path as a default module replaces it |
| `_data/` | Files that run after the default `_data` ones, like vehicle trunk sizes |
| `components.json` | Weapon components changed from the admin menu |
| `_backups/` | A copy of `items.lua` before every change made from the admin menu |

<Note>
  `jaksam_inventory_data` doesn't need a line in `server.cfg`: `jaksam_inventory` starts it by itself.
</Note>

### Troubleshooting

<AccordionGroup>
  <Accordion title="The console says jaksam_inventory_data is missing">
    `jaksam_inventory_data` must be next to `jaksam_inventory`, in the same folder. Put yours back (or restore it from your backup) and restart the server. If you never had one, an empty one has been created for you: just restart.
  </Accordion>

  <Accordion title="The console asks me to update jaksam_core">
    Your `jaksam_core` is too old to read the settings from `jaksam_inventory_data`. Download the latest `jaksam_core` and replace it. Until then, your settings keep working from their old place.
  </Accordion>

  <Accordion title="The console says a file in jaksam_inventory was edited">
    That change will be lost with the next update. Move it to the place the console tells you, inside `jaksam_inventory_data`.
  </Accordion>
</AccordionGroup>

## Moving from 1.27 or older to 1.28

You only do this once. After it, every update is the simple one above.

<Steps>
  <Step title="Stop your server and back up">
    Stop your server and make a copy of your whole `jaksam_inventory` folder.
  </Step>
  <Step title="Update jaksam_core too">
    Download the latest `jaksam_core` and replace yours. Older versions can't read the settings from their new place.
  </Step>
  <Step title="Copy the new version over the old one">
    Copy the new `jaksam_inventory` **over** your current one, overwriting the files, and put `jaksam_inventory_data` from the download next to it.

    Don't delete the old folder first: your old files must still be inside `jaksam_inventory` on the first start, so they can be moved. If you already deleted it, copy `current_config.json`, `_data/`, `_hooks/`, `_modules/`, `integrations/`, `locales/` and your custom images in `_images/` from your backup into the new `jaksam_inventory` before starting.
  </Step>
  <Step title="Start your server">
    On the first start your settings, items, hooks, modules, integrations, translations and custom images are imported into `jaksam_inventory_data` automatically. The server console and the `/inventory` menu show what was imported, and the old files are moved to `jaksam_inventory/_migrated`.
  </Step>
</Steps>

<Note>
  Two things are not moved automatically:

  - **Custom colors** from `dist/assets/variables.css`: open the theme menu and set your theme as the server default, or copy the variables you changed into `jaksam_inventory_data/variables.css`
  - **Custom menu translations** in `dist/menu_translations/`: these are still inside `jaksam_inventory`, so copy them back after every update
</Note>

## Versions before 1.28

<Info>
  This is the guide for installations still on version 1.27 or older, where your customizations are inside the `jaksam_inventory` folder itself.
</Info>

<Warning>
  **Always create a backup before updating.** Never delete your existing installation before you have a working backup.
</Warning>

### Before You Start

<Tip>
  **Recommended:** Keep your backup for at least a few days after the update. This makes it easy to roll back if something goes wrong.
</Tip>

<CardGroup cols={2}>
  <Card title="Stop Your Server" icon="server">
    Always stop your FiveM server before replacing the inventory files.
  </Card>

  <Card title="Create a Backup" icon="floppy-disk">
    Back up your customized files and folders before installing the new version.
  </Card>

  <Card title="Install the Update" icon="download">
    Remove the old version and upload the latest Jaksam Inventory release.
  </Card>

  <Card title="Restore Customizations" icon="rotate">
    Restore your backed-up files to the new installation.
  </Card>
</CardGroup>

### What Should I Back Up?

#### Always Back Up

These files and folders should **always** be included in your backup:

| File / Folder | Description |
| --- | --- |
| `_data/` | Items and inventory settings |
| `_backups/` | Item list backups |
| `_hooks/` | Crafting recipes and custom logic |
| `_modules/` | Integrations with external scripts |
| `integrations/` | Integration settings |
| `current_config.json` | Main configuration file |

#### Custom Files

Only back these up if you have modified or added them:

| File / Folder | Description |
| --- | --- |
| `_images/` | Custom item images |
| `dist/assets/variables.css` | Custom theme colors |
| `_locales/` | Custom translations |
| `dist/menu_translations/` | Custom menu translations |

<Note>
  If you haven't customized any of the files listed above, you don't need to back them up.
</Note>

### Update Process

Follow these steps **in order**.

### Quick Reference

| File / Folder | Backup Required | Purpose |
| --- | :-: | --- |
| `_data/` | Yes | Items and settings |
| `_backups/` | Yes | Item list backups |
| `_hooks/` | Yes | Crafting and custom logic |
| `_modules/` | Yes | External integrations |
| `integrations/` | Yes | Integration settings |
| `current_config.json` | Yes | Main configuration |
| `_images/` | Custom | Custom item images |
| `dist/assets/variables.css` | Custom | Theme customization |
| `_locales/` | Custom | Custom translations |
| `dist/menu_translations/` | Custom | Menu translations |

### Troubleshooting

<AccordionGroup>
  <Accordion title="My items disappeared">
    Restore the `_data/` folder from your backup and restart the server.
  </Accordion>

  <Accordion title="My crafting recipes are missing">
    Restore the `_hooks/` folder from your backup.
  </Accordion>

  <Accordion title="My settings were reset">
    Restore `current_config.json` from your backup.
  </Accordion>

  <Accordion title="My theme colors were reset">
    Restore `dist/assets/variables.css` from your backup if you customized the default theme.
  </Accordion>

  <Accordion title="My custom images are missing">
    Restore your customized `_images/` folder.
  </Accordion>

  <Accordion title="My translations are missing">
    Restore `_locales/` and/or `dist/menu_translations/`, depending on which translation files you customized.
  </Accordion>

  <Accordion title="My server won't start">
    1. Make sure the new `jaksam_inventory` folder is installed correctly.
    2. Make sure your backup files were restored to the correct locations.
    3. Wait approximately 30 seconds after starting the server, as the database may be updating automatically.
    4. Check your server console for errors.
    5. If the problem persists, restore your previous backup and contact support.
  </Accordion>
</AccordionGroup>

### Important

<Warning>
  **Never delete your backup immediately after a successful update.** Keep it for a few days in case you discover an issue later.
</Warning>

<Check>
  Once everything is working correctly, your Jaksam Inventory update is complete.
</Check>
