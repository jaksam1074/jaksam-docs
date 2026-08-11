---
title: "How to"
description: "Schritt-für-Schritt-Datenbank- und Script-Updates, die beim Upgrade von Jobs Creator von einer älteren Version nötig sind."
icon: "clock-rotate-left"
tag: "Update"
---

Dieser Abschnitt erklärt, wie man das Script von alten Versionen aktualisiert.

<Warning>
  Du musst **alle Schritte** von deiner _aktuellen Version_ bis zur _neueren_ befolgen.
</Warning>

<Tip>
  Ein **Backup** wird vor diesen Schritten immer empfohlen.
</Tip>

<Tabs>
  <Tab title="3.5">
    Füge folgenden Code in `jobs_creator/integrations/sv_integrations.lua` ein und nutze den Befehl in der Serverkonsole oder im Spiel (es gibt eine Ausgabe, wenn du den Befehl nutzt).

    ```lua
    RegisterCommand('updateRecipes', function(playerId)
        if(playerId == 0 or isAllowed(playerId)) then
            MySQL.Async.fetchAll('SELECT id, data FROM jobs_data WHERE type="crafting_table"', {}, function(results)
                for k, result in pairs(results) do
                    local markerId = result.id
    
                    if(result.data) then
                        local data = json.decode(result.data)
    
                        local newData = {}
    
                        local anythingChanged = false
    
                        if(data.craftablesItems) then
                            for itemName, craftingData in pairs(data.craftablesItems) do
                                if(not craftingData.recipes) then
                                    anythingChanged = true
                                end
    
                                newData[itemName] = {
                                    recipes = craftingData,
                                    animations = {}
                                }
                            end
                        end
    
                        local markerData = {
                            craftablesItems = newData
                        }
    
                        if(anythingChanged) then
                            print("Updating marker ID: " .. markerId)
                            MySQL.Async.execute("UPDATE jobs_data SET data=@newData WHERE id=@markerId", {
                                ['@newData'] = json.encode(markerData),
                                ['@markerId'] = markerId
                            })
                        else
                            print("Marker ID " .. markerId .. " doesn't need to update")
                        end
                    end
                end
            end)
        end
    end)
    ```
  </Tab>
  <Tab title="3.8">
    Führe diese Abfrage in der Datenbank aus, um alte Job-Shop-Items zu konvertieren.

    ```sql
    ALTER TABLE job_shop ADD COLUMN IF NOT EXISTS `item_type` VARCHAR(50) NOT NULL AFTER item_name;
    UPDATE job_shop SET item_type = "item_standard";
    ```
  </Tab>
  <Tab title="3.11">
    Füge folgenden Code in `jobs_creator/integrations/sv_integrations.lua` ein und nutze den Befehl in der Serverkonsole oder im Spiel (es gibt eine Ausgabe, wenn du den Befehl nutzt).

    ```lua
    RegisterCommand('updateHarvest', function(playerId)
        if(playerId == 0 or isAllowed(playerId)) then
            MySQL.Async.fetchAll('SELECT id, data FROM jobs_data WHERE type="harvest"', {}, function(results)
                for k, result in pairs(results) do
                    local markerId = result.id
                    local data = json.decode(result.data)
    
                    local anythingChanged = false
    
                    if(data) then
                        if(data.itemQuantity) then
                            data.itemMinQuantity = data.itemQuantity
                            data.itemMaxQuantity = data.itemQuantity
                            data.itemQuantity = nil
    
                            anythingChanged = true
                        end
                    end
    
                    if(anythingChanged) then
                        print("Updating marker ID: " .. markerId)
                        MySQL.Async.execute("UPDATE jobs_data SET data=@newData WHERE id=@markerId", {
                            ['@newData'] = json.encode(data),
                            ['@markerId'] = markerId
                        })
                    else
                        print("Marker ID " .. markerId .. " doesn't need to update")
                    end
                end
            end)
        end
    end)
    ```
  </Tab>
  <Tab title="3.14">
    Führe diese Abfrage in der Datenbank aus, um alte Tabellen zu konvertieren und die neue zu erstellen.

    ```sql
    CREATE TABLE IF NOT EXISTS `jobs_wardrobes` (
        `id` INT(11) NOT NULL AUTO_INCREMENT,
        `identifier` VARCHAR(100) NOT NULL COLLATE 'utf8mb4_general_ci',
        `label` VARCHAR(50) NOT NULL COLLATE 'utf8mb4_general_ci',
        `outfit` LONGTEXT NOT NULL DEFAULT '' COLLATE 'utf8mb4_bin',
        PRIMARY KEY (`id`) USING BTREE,
        INDEX `identifier` (`identifier`) USING BTREE
    );
    
    RENAME TABLE
        job_armory TO jobs_armories,
        job_garage TO jobs_garages,
        job_shop TO jobs_shops;
    ```
  </Tab>
  <Tab title="3.16">
    Füge folgenden Code in `jobs_creator/integrations/sv_integrations.lua` ein und nutze den Befehl in der Serverkonsole oder im Spiel (es gibt eine Ausgabe, wenn du den Befehl nutzt).

    ```lua
    RegisterCommand('updateShops', function(playerId)
        if(playerId == 0 or isAllowed(playerId)) then
            MySQL.Async.fetchAll('SELECT id, data FROM jobs_data WHERE type="shop"', {}, function(results)
                for k, result in pairs(results) do
                    local markerId = result.id
                    local data = json.decode(result.data)
    
                    local anythingChanged = false
    
                    if(data and data.itemsOnSale) then
                        for itemName, itemData in pairs(data.itemsOnSale) do
                            if(type(itemData) == "number") then
                                data.itemsOnSale[itemName] = {
                                    price = itemData
                                }
    
                                anythingChanged = true
                            end
                        end
                    end
    
                    if(anythingChanged) then
                        print("Updating marker ID: " .. markerId)
                        MySQL.Async.execute("UPDATE jobs_data SET data=@newData WHERE id=@markerId", {
                            ['@newData'] = json.encode(data),
                            ['@markerId'] = markerId
                        })
                    else
                        print("Marker ID " .. markerId .. " doesn't need to update")
                    end
                end
            end)
        end
    end)
    ```
  </Tab>
  <Tab title="3.18">
    Füge folgenden Code in `jobs_creator/integrations/sv_integrations.lua` ein und nutze den Befehl in der Serverkonsole oder im Spiel (es gibt eine Ausgabe, wenn du den Befehl nutzt).

    ```lua
    RegisterCommand('updateHarvest2', function(playerId)
        if(playerId == 0 or isAllowed(playerId)) then
            MySQL.Async.fetchAll('SELECT id, data FROM jobs_data WHERE type="harvest"', {}, function(results)
                for k, result in pairs(results) do
                    local markerId = result.id
                    local data = json.decode(result.data)
    
                    local anythingChanged = false
    
                    if(data) then
                        if(data.itemName or data.itemMinQuantity or data.itemMaxQuantity) then
    
                            data.harvestableItems = {
                                {
                                    name = data.itemName,
                                    minQuantity = data.itemMinQuantity,
                                    maxQuantity = data.itemMaxQuantity,
                                    time = data.itemTime,
                                    chances = 100
                                }
                            }
    
                            data.itemMinQuantity = nil
                            data.itemMaxQuantity = nil
                            data.itemTime = nil
                            data.itemName = nil
    
                            anythingChanged = true
                        end
                    end
    
                    if(anythingChanged) then
                        print("Updating marker ID: " .. markerId)
                        MySQL.Async.execute("UPDATE jobs_data SET data=@newData WHERE id=@markerId", {
                            ['@newData'] = json.encode(data),
                            ['@markerId'] = markerId
                        })
                    else
                        print("Marker ID " .. markerId .. " doesn't need to update")
                    end
                end
            end)
        end
    end)
    ```
  </Tab>
  <Tab title="4.0">
    <Note>
      Nachdem der Server läuft und das Script gestartet ist, führe diese Abfrage in der Datenbank aus.
    </Note>

    ```sql
    UPDATE jobs_data SET grades_type="minimumGrade" WHERE grades_type IS NULL;
    ```

    Füge folgenden Code in `jobs_creator/integrations/sv_integrations.lua` ein und nutze **beide Befehle** in der Serverkonsole oder im Spiel (es gibt eine Ausgabe, wenn du den Befehl nutzt).

    ```lua
    RegisterCommand('updateHarvest3', function(playerId)
        if(playerId == 0 or isAllowed(playerId)) then
            MySQL.Async.fetchAll('SELECT id, data FROM jobs_data WHERE type="harvest"', {}, function(results)
                for k, result in pairs(results) do
                    local markerId = result.id
                    local data = json.decode(result.data)
    
                    local anythingChanged = false
    
                    if(data) then
                        if(data.itemTool and not data.itemToolLoseProbability) then
                            data.itemToolLoseProbability = 100
                            anythingChanged = true
                        end
                    end
    
                    if(anythingChanged) then
                        print("Updating marker ID: " .. markerId)
                        MySQL.Async.execute("UPDATE jobs_data SET data=@newData WHERE id=@markerId", {
                            ['@newData'] = json.encode(data),
                            ['@markerId'] = markerId
                        })
                    else
                        print("Marker ID " .. markerId .. " doesn't need to update")
                    end
                end
            end)
        end
    end)
    
    RegisterCommand('updateMarkets', function(playerId)
        if(playerId == 0 or isAllowed(playerId)) then
            MySQL.Async.fetchAll('SELECT id, data FROM jobs_data WHERE type="market"', {}, function(results)
                for k, result in pairs(results) do
                    local markerId = result.id
                    local data = json.decode(result.data)
    
                    local anythingChanged = false
    
                    if(data and data.items) then
                        for itemName, itemData in pairs(data.items) do
                            if(itemData.price) then
                                itemData.maxPrice = itemData.price
                                itemData.minPrice = itemData.price
                                itemData.price = nil
    
                                anythingChanged = true
                            end
                        end
                    end
    
                    if(anythingChanged) then
                        print("Updating marker ID: " .. markerId)
                        MySQL.Async.execute("UPDATE jobs_data SET data=@newData WHERE id=@markerId", {
                            ['@newData'] = json.encode(data),
                            ['@markerId'] = markerId
                        })
                    else
                        print("Marker ID " .. markerId .. " doesn't need to update")
                    end
                end
            end)
        end
    end)
    ```
  </Tab>
  <Tab title="8.0">
    Füge folgenden Code in `jobs_creator/integrations/sv_integrations.lua` ein, speichere und starte das Script neu, und nutze dann **den Befehl** in der **Serverkonsole**.

    ```lua
    -- CONVERT FROM 7.11 to 8.0
    RegisterCommand("upgrade_to_8", function(playerId)
        if(playerId ~= 0) then return end -- Nur für die Serverkonsole
    
        local conversionCount = 0
    
        print("^3Converting to 8.0^7")
    
        local results = MySQL.Sync.fetchAll("SELECT * FROM jobs_data WHERE type='shop' OR type='market' OR type='harvest' OR type='process' OR type='crafting_table'")
    
        print("^3Automatically verifying " .. #results .. " markers^7")
    
        for i=1, #results do
            local currentMarker = results[i]
            local markerData = json.decode(currentMarker.data)
            local hasToUpdate = markerData and true or false
    
            if(currentMarker.type == "shop" and hasToUpdate) then
                local newItemsOnSale = {}
                markerData.itemsOnSale = markerData.itemsOnSale or {}
    
                if(#markerData.itemsOnSale == 0) then
                    for itemName, content in pairs(markerData.itemsOnSale) do
                        local object = { label = itemName, type = itemName:sub(1, #"WEAPON") == "WEAPON" and "weapon" or "item", metadata = nil, name = itemName }
                        content.object = object
    
                        table.insert(newItemsOnSale, content)
                    end
    
                    markerData.itemsOnSale = newItemsOnSale
                else
                    hasToUpdate = false -- Nutzt bereits das Array, also schon auf 8.0
                end
            elseif(currentMarker.type == "market" and hasToUpdate) then
                local newItems = {}
                markerData.items = markerData.items or {}
    
                if(#markerData.items == 0) then
                    for itemName, content in pairs(markerData.items) do
                        local object = { label = itemName, type = itemName:sub(1, #"WEAPON") == "WEAPON" and "weapon" or "item", metadata = nil, name = itemName }
                        content.object = object
    
                        table.insert(newItems, content)
                    end
    
                    markerData.items = newItems
                else
                    hasToUpdate = false -- Nutzt bereits das Array, also schon auf 8.0
                end
    
            elseif(currentMarker.type == "harvest" and hasToUpdate) then
                local newHarvestableItems = {}
                markerData.harvestableItems = markerData.harvestableItems or {}
    
                for i=1, #markerData.harvestableItems do
                    local harvestableItem = markerData.harvestableItems[i]
    
                    if(harvestableItem.name and hasToUpdate) then
                        local object = { label = harvestableItem.name, type = harvestableItem.name:sub(1, #"WEAPON") == "WEAPON" and "weapon" or "item", metadata = nil, name = harvestableItem.name }
    
                        harvestableItem.object = object
                        harvestableItem.name = nil
                        harvestableItem.itemTool = nil
    
                        table.insert(newHarvestableItems, harvestableItem)
                    else
                        hasToUpdate = false
                    end
                end
    
                if(hasToUpdate) then
                    if(markerData.itemTool) then
                        local toolObject = { label = markerData.itemTool, type = markerData.itemTool:sub(1, #"WEAPON") == "WEAPON" and "weapon" or "item", metadata = nil, name = markerData.itemTool }
                        markerData.itemTool = toolObject
                    end
                    markerData.harvestableItems = newHarvestableItems
                end
            elseif(currentMarker.type == "process" and hasToUpdate) then
                if(markerData.itemToAddName) then
                    local itemToAdd = { label = markerData.itemToAddName, type = markerData.itemToAddName:sub(1, #"WEAPON") == "WEAPON" and "weapon" or "item", metadata = nil, name = markerData.itemToAddName }
                    local itemToRemove = { label = markerData.itemToRemoveName, type = markerData.itemToRemoveName:sub(1, #"WEAPON") == "WEAPON" and "weapon" or "item", metadata = nil, name = markerData.itemToRemoveName }
    
                    markerData.itemToAddName = nil
                    markerData.itemToRemoveName = nil
    
                    markerData.itemToAdd = itemToAdd
                    markerData.itemToRemove = itemToRemove
                else
                    hasToUpdate = false
                end
            elseif(currentMarker.type == "crafting_table" and hasToUpdate) then
                local newCraftablesItems = {}
                markerData.craftablesItems = markerData.craftablesItems or {}
    
                if(#markerData.craftablesItems == 0) then
                    local foundAnything = false
                    for itemName, content in pairs(markerData.craftablesItems) do
                        local resultObject = { label = itemName, type = itemName:sub(1, #"WEAPON") == "WEAPON" and "weapon" or "item", metadata = nil, name = itemName }
                        content.resultObject = resultObject
    
                        local newRecipes = {}
                        for ingredientName, ingredientContent in pairs(content.recipes) do
                            local ingredientObject = { label = ingredientName, type = ingredientName:sub(1, #"WEAPON") == "WEAPON" and "weapon" or "item", metadata = nil, name = ingredientName }
                            ingredientContent.object = ingredientObject
    
                            table.insert(newRecipes, ingredientContent)
                        end
    
                        content.recipes = newRecipes
    
                        table.insert(newCraftablesItems, content)
    
                        foundAnything = true
                    end
    
                    if(foundAnything) then
                        markerData.craftablesItems = newCraftablesItems
                    else
                        hasToUpdate = false
                    end
                else
                    hasToUpdate = false -- Nutzt bereits das Array, also schon auf 8.0
                end
            end
    
            if(hasToUpdate) then
                print("UPDATING MARKER ", currentMarker.id)
                currentMarker.data = json.encode(markerData)
    
                local affectedRows = MySQL.Sync.execute("UPDATE jobs_data SET data=@data WHERE id=@id", {
                    ["@data"] = currentMarker.data,
                    ["@id"] = currentMarker.id
                })
    
                if(affectedRows > 0) then
                    conversionCount = conversionCount + 1
                end
            end
        end
    
        if(conversionCount > 0) then
            print("^2Converted ^3" .. conversionCount .. "^2 markers successfully, restart the script!^7")
        else
            print("^3No markers to convert^7")
        end
    end)
    ```
  </Tab>
</Tabs>
