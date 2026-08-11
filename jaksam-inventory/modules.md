---
title: "Modules"
description: "Replace default features like gangs, progress bar, text UI, and logs with your own custom modules."
icon: "puzzle-piece"
---

Modules are an easy way for Jaksam Inventory to replace certain default features (gangs, progress bar, text UI, logs).

To choose an existing module, open the `/inventory` admin menu, go to settings, and choose it. As easy as that.

### Available Modules

| Category | Available Options |
| --- | --- |
| Gangs | `default` |
| Logs | `custom`, `jaksam` |
| Progress Bar | `jaksam`, `ox_lib`, `qb-core` |
| Text UI | `esx`, `none`, `ox_lib` |

### Creating a Custom Module

Pick the category you want to create a module for. Each tab walks you through the exact steps for that category and gives you a ready-to-edit template.

<Tabs>
  <Tab title="Gangs">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `jaksam_inventory/_modules/gangs` folder.
      </Step>
      <Step title="Duplicate an existing module">
        Copy an existing module (e.g. `default`) and paste it in the same folder as a template.
      </Step>
      <Step title="Rename the copy">
        Rename the pasted copy to match the integration you want to create.
      </Step>
      <Step title="Implement the required functions">
        Open the renamed file and edit it to match the events of the third-party script you're integrating:

        ```lua
        local moduleType = "gangs"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Checks if a player has gang permission based on their gang and grade level, SERVER SIDE
        -- allowedGangs format: { gangName = true } (all grades allowed) or { gangName = { ["0"] = true, ["1"] = true } } (specific grades)
        Integrations[moduleType][moduleName].isPlayerGangAllowed = function(playerId, allowedGangs)
            -- Add your code here
        end

        -- Same check, but CLIENT SIDE
        Integrations[moduleType][moduleName].isClientGangAllowed = function(allowedGangs)
            -- Add your code here
        end

        -- Returns all gangs available in the game (see an existing module for the exact table format)
        Integrations[moduleType][moduleName].getAllGangs = function()
            -- Add your code here
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Logs">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `jaksam_inventory/_modules/logs` folder.
      </Step>
      <Step title="Duplicate an existing module">
        Copy an existing module (e.g. `jaksam`) and paste it in the same folder as a template.
      </Step>
      <Step title="Rename the copy">
        Rename the pasted copy to match the integration you want to create.
      </Step>
      <Step title="Implement the required functions">
        Open the renamed file and edit it to match the events of the third-party script you're integrating:

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
      </Step>
    </Steps>
  </Tab>

  <Tab title="Progress Bar">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `jaksam_inventory/_modules/progressbar` folder.
      </Step>
      <Step title="Duplicate an existing module">
        Copy an existing module (e.g. `jaksam`) and paste it in the same folder as a template.
      </Step>
      <Step title="Rename the copy">
        Rename the pasted copy to match the integration you want to create.
      </Step>
      <Step title="Implement the required functions">
        Open the renamed file and edit it to match the events of the third-party script you're integrating:

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
      </Step>
    </Steps>
  </Tab>

  <Tab title="Text UI">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `jaksam_inventory/_modules/textui` folder.
      </Step>
      <Step title="Duplicate an existing module">
        Copy an existing module (e.g. `ox_lib`) and paste it in the same folder as a template.
      </Step>
      <Step title="Rename the copy">
        Rename the pasted copy to match the integration you want to create.
      </Step>
      <Step title="Implement the required functions">
        Open the renamed file and edit it to match the events of the third-party script you're integrating:

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
      </Step>
    </Steps>
  </Tab>
</Tabs>
