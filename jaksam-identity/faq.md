---
title: "FAQ"
description: "Frequently asked questions specific to Jaksam Identity, covering workshops, raids, documents, qb-inventory seals and integrations."
icon: "circle-question"
---

This page has FAQs related **ONLY to this script**. Be sure to also check the [common FAQ](/jaksams-scripts/common-faq) for other issues.

<AccordionGroup>
  <Accordion title="I can't find any forgery workshop in the world">
    No workshop is configured out of the box, so the whole forgery side stays invisible until you add one.

    Add them in `Config.Forgery.workshops` (`config/forgery.lua`), or in game on the workshop page of `/documents config`. See [Forgery workshops](/jaksam-identity/guides/forgery-workshops).
  </Accordion>

  <Accordion title="The workshop interior is empty or invisible">
    The workshop uses the biker fake ID interior from `bob74_ipl`. Make sure `bob74_ipl` is installed and started **before** `jksm_identity`. The console names it in red at start if it is missing.
  </Accordion>

  <Accordion title="Officers can't seize anything during a raid">
    Every force needs an evidence locker. Place it on the Raids page of `/documents config`, or set `locker` in `Config.Raid.forces`. Without one nothing can be seized.
  </Accordion>

  <Accordion title="Officers or guests inside a workshop don't see the stations">
    That's intended. Only members of the owning job see and use the stations, computers and laptops. Officers get their own options during a raid: seize at the shelves and at the boss laptop, seal at the door.
  </Accordion>

  <Accordion title="Two ID cards open at the same time (Qbox)">
    `qbx_idcard` is still running. Remove it: Jaksam Identity answers in its place, so qbx_core's starter items and qbx_cityhall keep working unchanged.
  </Accordion>

  <Accordion title="The right-click actions View, Show and Copy number are missing (jaksam_inventory)">
    Copy `install/jaksam_item_types.lua` to `jaksam_inventory_data/_data/jksm_identity.lua` and restart `jaksam_inventory` once. See [Installation](/jaksam-identity/installation#add-the-items).
  </Accordion>

  <Accordion title="Documents show nothing and say the seal is invalid (qb-inventory)">
    qb-inventory takes an item's data from the client, so every document carries a seal made with a key only the server knows, kept in the `jksm_identity_settings` table.

    If you moved or reset the database without that table, the key changed and the existing documents lost their seal. Restore the table from your backup, or issue the documents again.
  </Accordion>

  <Accordion title="The starter ID card has no photo">
    That's intended. Starter documents are issued right after the character loads, without a photo. The photo is taken at a [citizen office](/jaksam-identity/guides/citizen-offices) with a renewal.
  </Accordion>

  <Accordion title="Documents bought in a shop are detected as forgeries">
    A document made by a shop or an admin give is registered (real), unless its jaksam `rarity` is listed in `Config.UnregisteredRarities` (default `illegal`). Change the item's rarity, or remove that rarity from the list.
  </Accordion>

  <Accordion title="Expired or suspended documents can still be used">
    That's intended: **facts, not force**. Expiry, suspensions and old photos are shown on the card and in the register check, but nothing is removed, blocked or renewed automatically. What follows is roleplay.
  </Accordion>

  <Accordion title="Can the police find out who made a forgery?">
    No. The register check shows only what an authority would know: no record, status, expiry, missing licences, data mismatch. Who made it and its quality are only visible to admins with `/documents truth <serial>`. Who actually presented a document is written to `jksm_identity_log`, for admins only.
  </Accordion>

  <Accordion title="How do I add another document or licence?">
    Add the item to your inventory, then one entry in `Config.Documents` (`config/documents.lua`). Any licence your framework knows can become a document. See [Add your own document](/jaksam-identity/guides/documents-and-register#add-your-own-document).
  </Accordion>

  <Accordion title="How do I change the language or add a new one?">
    `Config.Locale` picks the language (`en` and `de` ship with the script), and admins can switch it in game in `/documents config`. To add a language, copy `locales/en.lua` to `locales/<code>.lua`, change `Locales['en']` to `Locales['<code>']`, translate the texts and set the code in `Config.Locale`. Missing keys fall back to English.
  </Accordion>

  <Accordion title="How do I use my own notifications, progress bar or minigame?">
    - Notifications: `bridge/notify.lua`, see [Notifications](/jaksam-identity/client/replace-notifications)
    - Progress bar: `Editable.Progress` in `editable/client.lua`, see [Progress bar](/jaksam-identity/client/progress-bar)
    - Minigame: `Editable.SkillCheck` in `editable/client.lua`, see [Skill check](/jaksam-identity/client/skill-check)
  </Accordion>

  <Accordion title="Is esx_dmvschool safe to use with this script?">
    esx_dmvschool's event `esx_dmvschool:addLicense` is not checked on the server, so a cheating client can grant itself any licence with it. Jaksam Identity trusts the licences in the database. Secure that event in esx_dmvschool, or set `Config.DmvSchool.enabled = false`, on a live server.
  </Accordion>
</AccordionGroup>
