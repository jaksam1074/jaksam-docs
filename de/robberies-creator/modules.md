---
title: "Module"
description: "Ersetze Standard-Funktionen wie Fortschrittsbalken, Dispatch und Logs durch deine eigenen Module."
icon: "puzzle-piece"
---

Module sind ein einfacher Weg für Robberies Creator, bestimmte Standard-Funktionen (Fortschrittsbalken, Dispatch, Logs) zu ersetzen.

Um ein bereits vorhandenes Modul auszuwählen, öffne das `/robberiescreator`-Menü, gehe zu den Einstellungen und wähle es aus. Das war's schon.

### Verfügbare Module

| Kategorie | Verfügbare Optionen |
| --- | --- |
| Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Logs | `custom`, `jaksam` |
| Fortschrittsbalken | `jaksam`, `ox_lib`, `qb-core` |
| Text UI | `esx`, `none`, `ox_lib` |

### Ein eigenes Modul erstellen

Wähle die Kategorie, für die du ein Modul erstellen möchtest. Jeder Tab führt dich durch die genauen Schritte für diese Kategorie und liefert dir eine fertige Vorlage zum Bearbeiten.

<Tabs>
  <Tab title="Dispatch">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `robberies_creator/_modules/dispatch`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `default`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst:

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
      </Step>
    </Steps>
  </Tab>

  <Tab title="Logs">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `robberies_creator/_modules/logs`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `jaksam`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst:

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
      </Step>
    </Steps>
  </Tab>

  <Tab title="Fortschrittsbalken">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `robberies_creator/_modules/progressbar`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `jaksam`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst:

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
      </Step>
    </Steps>
  </Tab>

  <Tab title="Text UI">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `robberies_creator/_modules/textui`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `ox_lib`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst:

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
      </Step>
    </Steps>
  </Tab>
</Tabs>
