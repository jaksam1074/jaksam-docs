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

Jede Modul-Kategorie muss einen bestimmten Satz an Funktionen implementieren. Nutze ein vorhandenes Modul als Vorlage und übernimm diese Signaturen:

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

  <Accordion title="Menü">
    ```lua
    Integrations[moduleType][moduleName].open = function(id, title, elements, onSelect, onClose)
    Integrations[moduleType][moduleName].closeAll = function()
    Integrations[moduleType][moduleName].askQuantity = function(title, min, max)
    Integrations[moduleType][moduleName].askInput = function(title)
    ```
  </Accordion>

  <Accordion title="Fortschrittsbalken">
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
