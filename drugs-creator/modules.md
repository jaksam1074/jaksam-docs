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

### Required Functions

Each module category must implement a specific set of functions. Use an existing module as a template and match these signatures:

<AccordionGroup>
  <Accordion title="Dispatch">
    ```lua
    Integrations[moduleType][moduleName].alertPoliceServerSide = function(coords, message, category)
    Integrations[moduleType][moduleName].alertPoliceMemberClientSide = function(coords, message, category)
    ```
  </Accordion>

  <Accordion title="Gangs">
    ```lua
    Integrations[moduleType][moduleName].isPlayerGangAllowed = function(playerId, allowedGangs)
    Integrations[moduleType][moduleName].isClientGangAllowed = function(allowedGangs)
    Integrations[moduleType][moduleName].getPlayerGangName = function(playerId)
    Integrations[moduleType][moduleName].getClientGangName = function()
    Integrations[moduleType][moduleName].getAllGangs = function()
    ```
  </Accordion>

  <Accordion title="Inventory">
    ```lua
    Integrations[moduleType][moduleName].getSlotIdWithItem = function(playerId, itemName, metadata)
    Integrations[moduleType][moduleName].setItemMetadata = function(playerId, slotId, metadata)
    Integrations[moduleType][moduleName].getSlotItem = function(playerId, slotId)
    ```
  </Accordion>

  <Accordion title="Logs">
    ```lua
    Integrations[moduleType][moduleName].log = function(playerId, title, description, type, logType)
    ```
  </Accordion>

  <Accordion title="Menu">
    ```lua
    Integrations[moduleType][moduleName].open = function(id, title, elements, onSelect, onClose)
    Integrations[moduleType][moduleName].closeAll = function()
    Integrations[moduleType][moduleName].askQuantity = function(title, min, max)
    Integrations[moduleType][moduleName].askInput = function(title)
    ```
  </Accordion>

  <Accordion title="Progress Bar">
    ```lua
    Integrations[moduleType][moduleName].start = function(time, text, hexColor)
    Integrations[moduleType][moduleName].stop = function()
    ```
  </Accordion>

  <Accordion title="Stash">
    Client:
    ```lua
    Integrations[moduleType][moduleName].open = function(stashId)
    ```
    Server:
    ```lua
    Integrations[moduleType][moduleName].register = function(options)
    Integrations[moduleType][moduleName].addItem = function(stashId, itemName, amount, metadata)
    Integrations[moduleType][moduleName].removeItem = function(stashId, itemName, amount, metadata)
    Integrations[moduleType][moduleName].getItemCount = function(stashId, itemName)
    Integrations[moduleType][moduleName].canAddItem = function(stashId, itemName, amount)
    Integrations[moduleType][moduleName].clearStash = function(stashId)
    ```
  </Accordion>

  <Accordion title="Text UI">
    ```lua
    Integrations[moduleType][moduleName].show = function(message)
    Integrations[moduleType][moduleName].hide = function()
    ```
  </Accordion>
</AccordionGroup>