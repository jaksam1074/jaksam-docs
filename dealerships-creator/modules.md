---
title: "Modules"
description: "Replace default features like banking, text UI, and logs with your own custom modules."
icon: "puzzle-piece"
---

Modules are an easy way for Dealerships Creator to replace certain default features (banking, text UI, logs).

To choose an existing module, open the `/dealershipscreator` menu, go to settings, and choose it. As easy as that.

### Available Modules

| Category | Available Options |
| --- | --- |
| Banking | `default`, `example`, `okokbanking` |
| Logs | `custom`, `jaksam` |
| Text UI | `esx`, `none`, `ox_lib` |

### Creating a Custom Module

Pick the category you want to create a module for. Each tab walks you through the exact steps for that category and gives you a ready-to-edit template.

<Tabs>
  <Tab title="Banking">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `dealerships_creator/_modules/banking` folder.
      </Step>
      <Step title="Duplicate an existing module">
        Copy an existing module (e.g. `example`) and paste it in the same folder as a template.
      </Step>
      <Step title="Rename the copy">
        Rename the pasted copy to match the integration you want to create.
      </Step>
      <Step title="Implement the required functions">
        Open the renamed file and edit it to match the events of the third-party script you're integrating:

        ```lua
        local moduleType = "banking"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Returns the current money balance of the given society/business account
        Integrations[moduleType][moduleName].getSocietyMoney = function(societyName)
            -- Add your code here
        end

        -- Adds money to the given society/business account
        Integrations[moduleType][moduleName].giveMoneyToSociety = function(societyName, amount)
            -- Add your code here
        end

        -- Removes money from the given society/business account
        Integrations[moduleType][moduleName].removeMoneyFromSociety = function(societyName, amount)
            -- Add your code here
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Logs">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `dealerships_creator/_modules/logs` folder.
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

  <Tab title="Text UI">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `dealerships_creator/_modules/textui` folder.
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
