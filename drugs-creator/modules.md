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

Each module category expects a specific set of functions. Below is a minimal template for each category, based on the module registration boilerplate every module needs plus the functions that category must implement:

<AccordionGroup>
  <Accordion title="Dispatch">
    ```lua
    local moduleType = "dispatch"
    local moduleName = "yourModuleName" -- Rename to match the integration you're creating

    -- Don't touch, required to appear in in-game settings
    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Runs once per call, server side
    Integrations[moduleType][moduleName].alertPoliceServerSide = function(coords, message, category)
        if not IsDuplicityVersion() then return end

        -- Add your code here (e.g. call your dispatch script's export/event to alert police)
    end

    -- Runs client side, on every police officer's client
    Integrations[moduleType][moduleName].alertPoliceMemberClientSide = function(coords, message, category)
        if IsDuplicityVersion() then return end

        -- Add your code here (e.g. show a blip/notification to the officer)
    end
    ```
  </Accordion>

  <Accordion title="Gangs">
    ```lua
    local moduleType = "gangs"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    --- Checks if a player has gang permission based on their gang and grade level, SERVER SIDE
    --- @param playerId number - The server ID of the player
    --- @param allowedGangs table<string, boolean|table<string, boolean>> - Table of allowed gangs and their grades
    --- @return boolean|nil - Whether the player has permission
    Integrations[moduleType][moduleName].isPlayerGangAllowed = function(playerId, allowedGangs)
        -- Add your code here
    end

    --- Same check, but CLIENT SIDE
    --- @param allowedGangs table<string, boolean|table<string, boolean>>
    --- @return boolean|nil
    Integrations[moduleType][moduleName].isClientGangAllowed = function(allowedGangs)
        -- Add your code here
    end

    --- Returns the gang name for a player, SERVER SIDE
    --- @param playerId number
    --- @return string|nil
    Integrations[moduleType][moduleName].getPlayerGangName = function(playerId)
        -- Add your code here
    end

    --- Returns the gang name for the local player, CLIENT SIDE
    --- @return string|nil
    Integrations[moduleType][moduleName].getClientGangName = function()
        -- Add your code here
    end

    --- Returns all gangs available in the game
    --- @return table<string, { label: string, grades: table<number, { grade: number, label: string }> }>
    Integrations[moduleType][moduleName].getAllGangs = function()
        -- Add your code here
    end
    ```
  </Accordion>

  <Accordion title="Inventory">
    ```lua
    local moduleType = "inventory"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Returns the slot id that contains the given item, or nil if none
    Integrations[moduleType][moduleName].getSlotIdWithItem = function(playerId, itemName, metadata)
        -- Add your code here
    end

    -- Sets metadata on the item in the given slot
    Integrations[moduleType][moduleName].setItemMetadata = function(playerId, slotId, metadata)
        -- Add your code here
    end

    -- Returns the item data stored in the given slot
    Integrations[moduleType][moduleName].getSlotItem = function(playerId, slotId)
        -- Add your code here
    end
    ```
  </Accordion>

  <Accordion title="Logs">
    ```lua
    local moduleType = "logs"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Sends a log entry (e.g. to a Discord webhook or a custom logging script)
    Integrations[moduleType][moduleName].log = function(playerId, title, description, type, logType)
        -- Add your code here
    end
    ```
  </Accordion>

  <Accordion title="Menu">
    ```lua
    local moduleType = "menu"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Opens a menu with the given elements
    Integrations[moduleType][moduleName].open = function(id, title, elements, onSelect, onClose)
        -- Add your code here
    end

    -- Closes any menu opened by this module
    Integrations[moduleType][moduleName].closeAll = function()
        -- Add your code here
    end

    -- Prompts the player for a number between min and max
    Integrations[moduleType][moduleName].askQuantity = function(title, min, max)
        -- Add your code here
    end

    -- Prompts the player for free text input
    Integrations[moduleType][moduleName].askInput = function(title)
        -- Add your code here
    end
    ```
  </Accordion>

  <Accordion title="Progress Bar">
    ```lua
    local moduleType = "progressbar"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Starts a progress bar for the given time (ms), with the given text and color
    Integrations[moduleType][moduleName].start = function(time, text, hexColor)
        -- Add your code here
    end

    -- Stops/hides the progress bar
    Integrations[moduleType][moduleName].stop = function()
        -- Add your code here
    end
    ```
  </Accordion>

  <Accordion title="Stash">
    Client:
    ```lua
    local moduleType = "stash"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Opens the stash UI for the player
    Integrations[moduleType][moduleName].open = function(stashId)
        -- Add your code here
    end
    ```
    Server:
    ```lua
    -- Registers the stash so it exists and can be opened
    Integrations[moduleType][moduleName].register = function(options)
        -- Add your code here
    end

    -- Adds an item to the stash
    Integrations[moduleType][moduleName].addItem = function(stashId, itemName, amount, metadata)
        -- Add your code here
    end

    -- Removes an item from the stash
    Integrations[moduleType][moduleName].removeItem = function(stashId, itemName, amount, metadata)
        -- Add your code here
    end

    -- Returns how many of itemName are currently in the stash
    Integrations[moduleType][moduleName].getItemCount = function(stashId, itemName)
        -- Add your code here
    end

    -- Returns whether amount more of itemName would still fit in the stash
    Integrations[moduleType][moduleName].canAddItem = function(stashId, itemName, amount)
        -- Add your code here
    end

    -- Removes all items from the stash
    Integrations[moduleType][moduleName].clearStash = function(stashId)
        -- Add your code here
    end
    ```
  </Accordion>

  <Accordion title="Text UI">
    ```lua
    local moduleType = "textui"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Shows a text UI prompt with the given message
    Integrations[moduleType][moduleName].show = function(message)
        -- Add your code here
    end

    -- Hides the text UI prompt
    Integrations[moduleType][moduleName].hide = function()
        -- Add your code here
    end
    ```
  </Accordion>
</AccordionGroup>