---
title: "How to Update"
icon: "rectangle-new"
---

# Updating Jaksam Inventory

Keep your Jaksam Inventory installation up to date without losing your custom items, settings, integrations, or other customizations.

<Warning>
  **Always create a backup before updating.** Never delete your existing installation before you have a working backup.
</Warning>

## Before You Start

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

## What Should I Back Up?

### Always Back Up

These files and folders should **always** be included in your backup:

| File / Folder | Description |
| --- | --- |
| `_data/` | Items and inventory settings |
| `_backups/` | Item list backups |
| `_hooks/` | Crafting recipes and custom logic |
| `_modules/` | Integrations with external scripts |
| `integrations/` | Integration settings |
| `current_config.json` | Main configuration file |

### Custom Files

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

## Update Process

Follow these steps **in order**.

## Quick Reference

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

## Troubleshooting

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

## Important

<Warning>
  **Never delete your backup immediately after a successful update.** Keep it for a few days in case you discover an issue later.
</Warning>

<Check>
  Once everything is working correctly, your Jaksam Inventory update is complete.
</Check>