---
title: "Modules"
description: "Replace default features like notify, progress bar, stash, and logs with your own custom modules."
icon: "puzzle-piece"
---

Modules are an easy way for Drugs Creator to replace certain default features (notify, progress bar, stash, logs).

To choose an existing module, open the `/drugscreator` menu, go to settings, and choose it. As easy as that.

### How to create a custom module?

Creating a module is extremely easy:

<Steps>
  <Step title="Navigate to the modules folder">
    Go to the `drugs_creator/_modules` folder.
  </Step>
  <Step title="Choose the module type">
    Pick the module type you want to create (logs, progressbar, stash, etc.).
  </Step>
  <Step title="Duplicate an existing module">
    Copy an existing module and paste it in the same folder as a template.
  </Step>
  <Step title="Rename the copy">
    Rename the pasted copy to match the integration you want to create.
  </Step>
  <Step title="Open the file">
    Open the newly renamed file.
  </Step>
  <Step title="Modify the events">
    Edit the file's content to match the events of the third-party script you're integrating.
  </Step>
</Steps>

### Available Modules

| Category | Available Options |
| --- | --- |
| Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Gangs | `default` |
| Inventory | `jaksam_inventory`, `ox_inventory`, `qb-inventory` |
| Logs | `custom`, `jaksam` |
| Menu | `menu_default`, `ox_context`, `ox_lib` |
| Progress Bar | `jaksam`, `ox_lib`, `qb-core` |
| Stash | `jaksam_inventory`, `ox-inventory`, `qb-inventory` |
| Text UI | `esx`, `none`, `ox_lib` |