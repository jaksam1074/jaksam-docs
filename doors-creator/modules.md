---
title: "Modules"
description: "Replace default features like lockpick, dispatch, and logs with your own custom modules."
icon: "puzzle-piece"
---

Modules are an easy way for Doors Creator to replace certain default features (lockpick, dispatch, logs).

To choose an existing module, open the `/doorscreator` menu, go to settings, and choose it. That's it.

### Available Modules

| Category | Available Options |
| --- | --- |
| Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Gangs | `default` |
| Lockpick | `default`, `ox_lib` |
| Logs | `custom`, `jaksam` |
| Progress Bar | `jaksam`, `ox_lib`, `qb-core` |
| Text UI | `esx`, `none`, `ox_lib` |

### Creating a Custom Module

Pick the category you want to create a module for. Each tab walks you through the exact steps for that category and gives you a ready-to-edit template.

<Tabs>
  <Tab title="Dispatch">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `doors_creator/_modules/dispatch` folder.
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
      </Step>
    </Steps>
  </Tab>

  <Tab title="Gangs">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `doors_creator/_modules/gangs` folder.
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

        -- Checks if a player has permission to open a door based on their gang and grade level, SERVER SIDE
        -- allowedGangs format: { gangName = true } (all grades allowed) or { gangName = { ["0"] = true, ["1"] = true } } (specific grades)
        Integrations[moduleType][moduleName].isPlayerGangAllowedToOpenDoor = function(playerId, allowedGangs)
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

  <Tab title="Lockpick">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `doors_creator/_modules/lockpick` folder.
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
        local moduleType = "lockpick"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Starts the lockpick minigame with the given number of attempts, and returns whether it succeeded
        Integrations[moduleType][moduleName].startLockpick = function(attempts)
            -- Add your code here
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Logs">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `doors_creator/_modules/logs` folder.
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
        Go to the `doors_creator/_modules/progressbar` folder.
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
        Go to the `doors_creator/_modules/textui` folder.
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
