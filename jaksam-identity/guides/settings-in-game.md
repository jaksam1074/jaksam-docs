---
title: "Settings in game"
description: "Change fees, offices, workshops, prices, wages and raid rules in game with /documents config, without a restart."
icon: "sliders"
---

Admins change most settings in game with `/documents config`: no file to edit, no restart.

## What is in it

| Section | Settings |
| --- | --- |
| **General** | Using and showing documents, document numbers, language |
| **Offices** | Starter documents, fees, the offices themselves |
| **Workshops** | The workshops with price and owner, rules for buying and selling, upgrade prices, material orders, storages, forging and order rules |
| **Workers** | Hiring fees, wages, working times, demo mode |
| **Raids** | Rules, forces with their evidence lockers, the door, seizure |

## How it works

- **Changes are collected and applied together.** What you change is marked, and a bar at the bottom saves it all (**Apply**) or drops it (**Discard**). Nothing reaches the players before that.
- **Places are set with the camera.** **Place** lets you walk around and aim: a ghost of the NPC stands where you look, the mouse wheel turns it, a click takes the place. **Here** takes the spot you stand on, and you can teleport to a saved place.
- **Jobs are picked from the framework's list.** Times are shown in seconds, minutes, hours or days, chances in percent.
- **In force at once** for everyone on the server after **Apply**. One marked exception waits for the next start of the script: the storage sizes.
- **The language** changes at once for everyone: menus, targets, blips and the labels in the config.

## Files and database

The config files stay the defaults. A changed value is kept in the database (table `jksm_identity_settings`) and wins over the file. Every value can go back to its default with one click, and every change is written to the log with the admin who made it.

<Note>
  These stay in `config/main.lua`, because they are needed while the script loads: framework, inventory and target, the admin rights, `Config.Debug` and the item names.
</Note>
