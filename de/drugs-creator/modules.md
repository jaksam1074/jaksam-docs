---
title: "Module"
description: "Ersetze Standard-Funktionen wie Notify, Fortschrittsbalken, Stash und Logs durch deine eigenen Module."
icon: "puzzle-piece"
---

Module sind ein einfacher Weg für Drugs Creator, bestimmte Standard-Funktionen (Notify, Fortschrittsbalken, Stash, Logs) zu ersetzen.

Um ein bereits vorhandenes Modul auszuwählen, öffne das `/drugscreator`-Menü, gehe zu den Einstellungen und wähle es aus. So einfach ist das.

### Wie erstelle ich ein eigenes Modul?

Ein Modul zu erstellen ist extrem einfach:

<Steps>
  <Step title="Zum Modules-Ordner navigieren">
    Gehe zum Ordner `drugs_creator/_modules`.
  </Step>
  <Step title="Modultyp auswählen">
    Wähle den Modultyp, den du erstellen möchtest (Logs, Fortschrittsbalken, Stash, usw.).
  </Step>
  <Step title="Vorhandenes Modul duplizieren">
    Kopiere ein vorhandenes Modul und füge es im gleichen Ordner als Vorlage ein.
  </Step>
  <Step title="Die Kopie umbenennen">
    Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
  </Step>
  <Step title="Die Datei öffnen">
    Öffne die neu umbenannte Datei.
  </Step>
  <Step title="Die Events anpassen">
    Bearbeite den Inhalt der Datei passend zu den Events des Drittanbieter-Scripts, das du integrierst.
  </Step>
</Steps>

### Verfügbare Module

| Kategorie | Verfügbare Optionen |
| --- | --- |
| Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Gangs | `default` |
| Inventory | `jaksam_inventory`, `ox_inventory`, `qb-inventory` |
| Logs | `custom`, `jaksam` |
| Menü | `menu_default`, `ox_context`, `ox_lib` |
| Fortschrittsbalken | `jaksam`, `ox_lib`, `qb-core` |
| Stash | `jaksam_inventory`, `ox-inventory`, `qb-inventory` |
| Text UI | `esx`, `none`, `ox_lib` |

### Benötigte Funktionen

Jede Modul-Kategorie erwartet einen bestimmten Satz an Funktionen. Unten findest du für jede Kategorie eine minimale Vorlage, basierend auf dem Registrierungs-Boilerplate, das jedes Modul braucht, plus den Funktionen, die diese Kategorie implementieren muss:

<AccordionGroup>
  <Accordion title="Dispatch">
    ```lua
    local moduleType = "dispatch"
    local moduleName = "yourModuleName" -- Passend zur Integration umbenennen, die du erstellst

    -- Nicht anfassen, wird benötigt damit es in den Ingame-Einstellungen erscheint
    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Läuft einmal pro Aufruf, server-seitig
    Integrations[moduleType][moduleName].alertPoliceServerSide = function(coords, message, category)
        if not IsDuplicityVersion() then return end

        -- Füge hier deinen Code ein (z.B. das Export/Event deines Dispatch-Scripts aufrufen, um die Polizei zu alarmieren)
    end

    -- Läuft client-seitig, auf jedem Client eines Polizei-Mitglieds
    Integrations[moduleType][moduleName].alertPoliceMemberClientSide = function(coords, message, category)
        if IsDuplicityVersion() then return end

        -- Füge hier deinen Code ein (z.B. dem Officer einen Blip/eine Benachrichtigung anzeigen)
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

    --- Prüft, ob ein Spieler anhand seiner Gang und seines Rangs berechtigt ist, SERVER-SEITIG
    --- @param playerId number - Die Server-ID des Spielers
    --- @param allowedGangs table<string, boolean|table<string, boolean>> - Tabelle erlaubter Gangs und deren Ränge
    --- @return boolean|nil - Ob der Spieler berechtigt ist
    Integrations[moduleType][moduleName].isPlayerGangAllowed = function(playerId, allowedGangs)
        -- Füge hier deinen Code ein
    end

    --- Gleiche Prüfung, aber CLIENT-SEITIG
    --- @param allowedGangs table<string, boolean|table<string, boolean>>
    --- @return boolean|nil
    Integrations[moduleType][moduleName].isClientGangAllowed = function(allowedGangs)
        -- Füge hier deinen Code ein
    end

    --- Gibt den Gang-Namen eines Spielers zurück, SERVER-SEITIG
    --- @param playerId number
    --- @return string|nil
    Integrations[moduleType][moduleName].getPlayerGangName = function(playerId)
        -- Füge hier deinen Code ein
    end

    --- Gibt den Gang-Namen des lokalen Spielers zurück, CLIENT-SEITIG
    --- @return string|nil
    Integrations[moduleType][moduleName].getClientGangName = function()
        -- Füge hier deinen Code ein
    end

    --- Gibt alle im Spiel verfügbaren Gangs zurück
    --- @return table<string, { label: string, grades: table<number, { grade: number, label: string }> }>
    Integrations[moduleType][moduleName].getAllGangs = function()
        -- Füge hier deinen Code ein
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

    -- Gibt den Slot zurück, der das angegebene Item enthält, oder nil falls keiner
    Integrations[moduleType][moduleName].getSlotIdWithItem = function(playerId, itemName, metadata)
        -- Füge hier deinen Code ein
    end

    -- Setzt die Metadaten des Items im angegebenen Slot
    Integrations[moduleType][moduleName].setItemMetadata = function(playerId, slotId, metadata)
        -- Füge hier deinen Code ein
    end

    -- Gibt die Item-Daten des angegebenen Slots zurück
    Integrations[moduleType][moduleName].getSlotItem = function(playerId, slotId)
        -- Füge hier deinen Code ein
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

    -- Sendet einen Log-Eintrag (z.B. an einen Discord-Webhook oder ein eigenes Logging-Script)
    Integrations[moduleType][moduleName].log = function(playerId, title, description, type, logType)
        -- Füge hier deinen Code ein
    end
    ```
  </Accordion>

  <Accordion title="Menü">
    ```lua
    local moduleType = "menu"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Öffnet ein Menü mit den angegebenen Elementen
    Integrations[moduleType][moduleName].open = function(id, title, elements, onSelect, onClose)
        -- Füge hier deinen Code ein
    end

    -- Schließt alle von diesem Modul geöffneten Menüs
    Integrations[moduleType][moduleName].closeAll = function()
        -- Füge hier deinen Code ein
    end

    -- Fragt den Spieler nach einer Zahl zwischen min und max
    Integrations[moduleType][moduleName].askQuantity = function(title, min, max)
        -- Füge hier deinen Code ein
    end

    -- Fragt den Spieler nach freier Texteingabe
    Integrations[moduleType][moduleName].askInput = function(title)
        -- Füge hier deinen Code ein
    end
    ```
  </Accordion>

  <Accordion title="Fortschrittsbalken">
    ```lua
    local moduleType = "progressbar"
    local moduleName = "yourModuleName"

    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Startet einen Fortschrittsbalken für die angegebene Zeit (ms), mit Text und Farbe
    Integrations[moduleType][moduleName].start = function(time, text, hexColor)
        -- Füge hier deinen Code ein
    end

    -- Stoppt/versteckt den Fortschrittsbalken
    Integrations[moduleType][moduleName].stop = function()
        -- Füge hier deinen Code ein
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

    -- Öffnet die Stash-UI für den Spieler
    Integrations[moduleType][moduleName].open = function(stashId)
        -- Füge hier deinen Code ein
    end
    ```
    Server:
    ```lua
    -- Registriert die Stash, damit sie existiert und geöffnet werden kann
    Integrations[moduleType][moduleName].register = function(options)
        -- Füge hier deinen Code ein
    end

    -- Fügt der Stash ein Item hinzu
    Integrations[moduleType][moduleName].addItem = function(stashId, itemName, amount, metadata)
        -- Füge hier deinen Code ein
    end

    -- Entfernt ein Item aus der Stash
    Integrations[moduleType][moduleName].removeItem = function(stashId, itemName, amount, metadata)
        -- Füge hier deinen Code ein
    end

    -- Gibt zurück, wie viele von itemName sich aktuell in der Stash befinden
    Integrations[moduleType][moduleName].getItemCount = function(stashId, itemName)
        -- Füge hier deinen Code ein
    end

    -- Gibt zurück, ob amount weitere itemName noch in die Stash passen würden
    Integrations[moduleType][moduleName].canAddItem = function(stashId, itemName, amount)
        -- Füge hier deinen Code ein
    end

    -- Entfernt alle Items aus der Stash
    Integrations[moduleType][moduleName].clearStash = function(stashId)
        -- Füge hier deinen Code ein
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

    -- Zeigt eine Text-UI-Meldung mit dem angegebenen Text
    Integrations[moduleType][moduleName].show = function(message)
        -- Füge hier deinen Code ein
    end

    -- Versteckt die Text-UI-Meldung
    Integrations[moduleType][moduleName].hide = function()
        -- Füge hier deinen Code ein
    end
    ```
  </Accordion>
</AccordionGroup>
