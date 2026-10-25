---
title: "Modules"
description: "Replace Boosting Creator default features like dispatch, vehicle keys, notifications, text UI, progress bar and skill check with your own modules."
icon: "puzzle-piece"
---

Modules are an easy way for Boosting Creator to work with the other scripts of your server: dispatch, vehicle keys, notifications and more.

To choose an existing module, open the `/boostingcreator` menu, go to **Settings > Modules**, and choose it. As easy as that.

### Available Modules

| Category | Available Options |
| --- | --- |
| Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Keys | `none`, `qb-vehiclekeys`, `vehicles_keys` |
| Logs | `jaksam` |
| Notify | `default`, `ox_lib` |
| Progress Bar | `jaksam`, `ox_lib` |
| Skill Check | `jaksam`, `ox_lib` |
| Text UI | `esx`, `none`, `ox_lib` |

<Info>
  **Keys** gives the thief temporary keys of the stolen car and takes them back when the contract ends. With `vehicles_keys` running, the car is also lockpicked and hotwired with vehicles_keys instead of the script's own break-in and hotwire.
</Info>

### Creating a Custom Module

<Steps>
  <Step title="Navigate to the modules folder">
    Go to the `boosting_creator/_modules/<category>` folder, for example `_modules/dispatch`.
  </Step>
  <Step title="Duplicate an existing module">
    Copy an existing module (for example `default`) and paste it in the same folder as a template.
  </Step>
  <Step title="Rename the copy">
    Rename the folder and the `moduleName` inside its files to match the script you are integrating.
  </Step>
  <Step title="Implement the functions">
    Edit the functions to call your script. For a dispatch:

    ```lua
    local moduleType = "dispatch"
    local moduleName = "yourModuleName"

    -- Don't touch, required to appear in the in-game settings
    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Server side, once per alert
    Integrations[moduleType][moduleName].alertPoliceServerSide = function(coords, message, category)
        if not IsDuplicityVersion() then return end

        -- Call your dispatch script's export or event here
    end
    ```

    The functions each category needs:

    | Category | Functions |
    | --- | --- |
    | Dispatch | `alertPoliceServerSide`, `alertPoliceMemberClientSide` |
    | Keys | `giveKeys`, `removeKeys` |
  </Step>
  <Step title="Restart and choose it">
    Restart the script, then pick your module in **Settings > Modules**.
  </Step>
</Steps>
