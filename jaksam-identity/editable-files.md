---
title: "Editable files"
description: "The files of Jaksam Identity that stay open in the escrowed release: config, locales, bridge and editable hooks."
icon: "file-pen"
---

Jaksam Identity has no `integrations` folder. Everything you can change stays open in the escrowed release, in these folders:

| Folder | What |
| --- | --- |
| `config/` | All settings |
| `locales/` | Texts, `Config.Locale` picks the language |
| `bridge/` | Inventory, target, notifications, phone (the framework bridge in `bridge/framework/` is escrowed) |
| `editable/` | Hooks: `CanIssue`, `OnIssued`, `CanEnterWorkshop`, `CanRaid`, `OnRaid`, `OnForged`, `OnLog`, `SkillCheck`, `Progress` |
| `install/` | Inventory items, item types, images, SQL |

## Editable hooks

<CardGroup cols={2}>
  <Card title="editable/server.lua" icon="server" href="/jaksam-identity/server/hooks">
    Server hooks: who may issue, enter a workshop or raid, and what happens after an issue, a forgery, a raid step or a log line.
  </Card>

  <Card title="editable/client.lua" icon="laptop" href="/jaksam-identity/client">
    Client hooks: the skill check at the forging stations and the progress bar.
  </Card>
</CardGroup>

Change the bodies to fit your server, but **keep the function names and arguments**.

## Bridge

`Config.Bridge` in `config/main.lua` picks the files in `bridge/`:

```lua
Config.Bridge = {
    framework = 'esx',          -- ESX version: 'esx' | QBCore version: 'auto' | 'qb' | 'qbox'
    inventory = 'jaksam',       -- 'jaksam' | 'ox_inventory' | 'qb-inventory' (QBCore version)
    target = 'ox_target',       -- 'ox_target' | QBCore version also 'qb-target' | 'auto'
    notify = 'esx',             -- 'esx' | 'qb' | 'qbox' | 'ox_lib' | QBCore version also 'auto'
    phone = 'roadphone',        -- 'roadphone' | 'none'
    menu = 'jksm',              -- 'jksm' (interaction card) | 'ox_lib' (context menu)
}
```

To support another inventory, the contract an inventory bridge must fulfil is documented at the top of `bridge/inventory/jaksam.lua`.
