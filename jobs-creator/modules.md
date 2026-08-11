---
title: "Modules"
description: "Replace default features like notify, progress bar, stash, and logs with your own custom modules."
icon: "puzzle-piece"
---

Modules are an easy way for Jobs Creator to replace certain default features (notify, progress bar, stash, logs).

To choose an existing module, open the `/jobscreator` menu, go to settings, and choose it. As easy as that.

### Available Modules

| Category | Available Options |
| --- | --- |
| Banking | `default`, `example`, `okok` |
| Boss | `default`, `example` |
| Logs | `custom`, `jaksam` |
| Notify | `default`, `example`, `origen`, `ox_lib` |
| Outfits | `default`, `illenium-appearance`, `rcore_clothing` |
| Progress Bar | `jaksam`, `ox_lib`, `qb-core` |
| Search Player | `jaksam`, `jaksam_inventory`, `ox_inventory` |
| Skillcheck | `jaksam`, `ox_lib` |
| Stash | `default`, `hc_inventory`, `jaksam_inventory`, `ox-inventory`, `qb-inventory` |
| Text UI | `esx`, `jg-text`, `none`, `ox_lib` |

### Creating a Custom Module

Pick the category you want to create a module for. Each tab walks you through the exact steps for that category and gives you a ready-to-edit template.

<Tabs>
  <Tab title="Banking">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `jobs_creator/_modules/banking` folder.
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

  <Tab title="Boss">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `jobs_creator/_modules/boss` folder.
      </Step>
      <Step title="Duplicate an existing module">
        Copy an existing module (e.g. `example`) and paste it in the same folder as a template.
      </Step>
      <Step title="Rename the copy">
        Rename the pasted copy to match the integration you want to create.
      </Step>
      <Step title="Implement the required functions">
        Open the renamed file and edit it to match the events of the third-party script you're integrating. All four functions are optional overrides: returning `nil` leaves the default Jobs Creator behavior untouched.

        ```lua
        local moduleType = "boss"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Called before returning the employees list to the client, return the (optionally modified) list
        Integrations[moduleType][moduleName].modifyEmployeesList = function(employeesArray, jobName)
            -- Add your code here

            return employeesArray
        end

        -- Called when an employee is fired. Return true if you handled it yourself, nil to keep the default behavior
        Integrations[moduleType][moduleName].fireEmployee = function(playerId, employeeIdentifier, jobName)
            -- Add your code here

            return nil
        end

        -- Called before recruiting a player. Return true if you handled it yourself, nil to keep the default behavior
        Integrations[moduleType][moduleName].recruitPlayer = function(playerId, targetId, jobName)
            -- Add your code here

            return nil
        end

        -- Called before changing an employee's grade. Return true if you handled it yourself, nil to keep the default behavior
        Integrations[moduleType][moduleName].changeGradeToEmployee = function(playerId, employeeIdentifier, newGrade, jobName)
            -- Add your code here

            return nil
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Logs">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `jobs_creator/_modules/logs` folder.
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

  <Tab title="Notify">
    <Steps>
      <Step title="Navigate to the modules folder">
        Go to the `jobs_creator/_modules/notify` folder.
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
        local moduleType = "notify"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Shows a notification with a plain message and an (optionally) colored version of it
        Integrations[moduleType][moduleName].showNotification = function(message, coloredMessage)
            -- Add your code here
        end
        ```
      </Step>
    </Steps>
  </Tab>
</Tabs>