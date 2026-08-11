---
title: "Module"
description: "Ersetze Standard-Funktionen wie Notify, Fortschrittsbalken, Stash und Logs durch deine eigenen Module."
icon: "puzzle-piece"
---

Module sind ein einfacher Weg für Jobs Creator, bestimmte Standard-Funktionen (Notify, Fortschrittsbalken, Stash, Logs) zu ersetzen.

Um ein bereits vorhandenes Modul auszuwählen, öffne das `/jobscreator`-Menü, gehe zu den Einstellungen und wähle es aus. So einfach ist das.

### Verfügbare Module

| Kategorie | Verfügbare Optionen |
| --- | --- |
| Banking | `default`, `example`, `okok` |
| Boss | `default`, `example` |
| Logs | `custom`, `jaksam` |
| Notify | `default`, `example`, `origen`, `ox_lib` |
| Outfits | `default`, `illenium-appearance`, `rcore_clothing` |
| Fortschrittsbalken | `jaksam`, `ox_lib`, `qb-core` |
| Search Player | `jaksam`, `jaksam_inventory`, `ox_inventory` |
| Skillcheck | `jaksam`, `ox_lib` |
| Stash | `default`, `hc_inventory`, `jaksam_inventory`, `ox-inventory`, `qb-inventory` |
| Text UI | `esx`, `jg-text`, `none`, `ox_lib` |

### Ein eigenes Modul erstellen

Wähle die Kategorie, für die du ein Modul erstellen möchtest. Jeder Tab führt dich durch die genauen Schritte für diese Kategorie und liefert dir eine fertige Vorlage zum Bearbeiten.

<Tabs>
  <Tab title="Banking">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/banking`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `example`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst:

        ```lua
        local moduleType = "banking"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Gibt den aktuellen Kontostand des angegebenen Society-/Business-Kontos zurück
        Integrations[moduleType][moduleName].getSocietyMoney = function(societyName)
            -- Füge hier deinen Code ein
        end

        -- Fügt dem angegebenen Society-/Business-Konto Geld hinzu
        Integrations[moduleType][moduleName].giveMoneyToSociety = function(societyName, amount)
            -- Füge hier deinen Code ein
        end

        -- Entfernt Geld vom angegebenen Society-/Business-Konto
        Integrations[moduleType][moduleName].removeMoneyFromSociety = function(societyName, amount)
            -- Füge hier deinen Code ein
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Boss">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/boss`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `example`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst. Alle vier Funktionen sind optionale Overrides: Ein Rückgabewert von `nil` lässt das Standardverhalten von Jobs Creator unverändert.

        ```lua
        local moduleType = "boss"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Wird aufgerufen, bevor die Mitarbeiterliste an den Client gesendet wird, gibt die (optional geänderte) Liste zurück
        Integrations[moduleType][moduleName].modifyEmployeesList = function(employeesArray, jobName)
            -- Füge hier deinen Code ein

            return employeesArray
        end

        -- Wird aufgerufen, wenn ein Mitarbeiter entlassen wird. Gib true zurück, wenn du es selbst behandelt hast, nil um das Standardverhalten beizubehalten
        Integrations[moduleType][moduleName].fireEmployee = function(playerId, employeeIdentifier, jobName)
            -- Füge hier deinen Code ein

            return nil
        end

        -- Wird aufgerufen, bevor ein Spieler rekrutiert wird. Gib true zurück, wenn du es selbst behandelt hast, nil um das Standardverhalten beizubehalten
        Integrations[moduleType][moduleName].recruitPlayer = function(playerId, targetId, jobName)
            -- Füge hier deinen Code ein

            return nil
        end

        -- Wird aufgerufen, bevor der Rang eines Mitarbeiters geändert wird. Gib true zurück, wenn du es selbst behandelt hast, nil um das Standardverhalten beizubehalten
        Integrations[moduleType][moduleName].changeGradeToEmployee = function(playerId, employeeIdentifier, newGrade, jobName)
            -- Füge hier deinen Code ein

            return nil
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Logs">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/logs`.
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

  <Tab title="Notify">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/notify`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `example`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst:

        ```lua
        local moduleType = "notify"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Zeigt eine Benachrichtigung mit einer einfachen Nachricht und (optional) einer farbigen Version davon
        Integrations[moduleType][moduleName].showNotification = function(message, coloredMessage)
            -- Füge hier deinen Code ein
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Outfits">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/outfits`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `rcore_clothing`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst. `openExternalMenu` steuert die anderen Funktionen: Gib `true` zurück, um die Outfit-UI vollständig durch dein eigenes Script zu ersetzen (nur `openWardrobe`/`openJobOutfits` werden verwendet), oder `false`, um weiterhin das Jobs-Creator-Menü zu nutzen (stattdessen werden `getPlayerClothes`/`setPlayerClothes` verwendet).

        ```lua
        local moduleType = "outfits"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Gib true zurück, um die Outfit-UI vollständig durch dein eigenes Script zu ersetzen, false um weiterhin das Jobs-Creator-Menü zu nutzen
        Integrations[moduleType][moduleName].openExternalMenu = function()
            return false
        end

        -- Öffnet das gespeicherte Spieler-Outfit-Menü deines Scripts (nur verwendet, wenn openExternalMenu true zurückgibt)
        Integrations[moduleType][moduleName].openWardrobe = function()
            -- Füge hier deinen Code ein
        end

        -- Öffnet das gespeicherte Job-Outfit-Menü deines Scripts und ersetzt damit vollständig die Job-Outfit-Funktion von Jobs Creator (nur verwendet, wenn openExternalMenu true zurückgibt)
        Integrations[moduleType][moduleName].openJobOutfits = function()
            -- Füge hier deinen Code ein
        end

        -- Gibt die aktuelle Outfit-/Kleidungstabelle des Spielers zurück (nur verwendet, wenn openExternalMenu false zurückgibt)
        Integrations[moduleType][moduleName].getPlayerClothes = function()
            -- Füge hier deinen Code ein
        end

        -- Wendet die angegebene Outfit-/Kleidungstabelle auf den Spieler an (nur verwendet, wenn openExternalMenu false zurückgibt)
        Integrations[moduleType][moduleName].setPlayerClothes = function(outfit, saveAfterRestart)
            -- Füge hier deinen Code ein
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Fortschrittsbalken">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/progressbar`.
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
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Search Player">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/search_player`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `ox_inventory`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst:

        ```lua
        local moduleType = "search_player"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Öffnet die Durchsuchen-/Inventar-UI des Zielspielers (z.B. nachdem geprüft wurde, ob er gefesselt ist)
        Integrations[moduleType][moduleName].search = function(targetServerId)
            -- Füge hier deinen Code ein
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Skillcheck">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/skillcheck`.
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
        local moduleType = "skillcheck"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Startet ein Skillcheck-Minigame mit der angegebenen Schwierigkeit und Geschwindigkeit
        Integrations[moduleType][moduleName].start = function(difficulty, speed)
            -- Füge hier deinen Code ein
        end

        -- Bricht das aktuell laufende Skillcheck-Minigame ab
        Integrations[moduleType][moduleName].cancel = function()
            -- Füge hier deinen Code ein
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Stash">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/stash`.
      </Step>
      <Step title="Vorhandenes Modul duplizieren">
        Kopiere ein vorhandenes Modul (z.B. `jaksam_inventory`) und füge es im gleichen Ordner als Vorlage ein.
      </Step>
      <Step title="Die Kopie umbenennen">
        Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
      </Step>
      <Step title="Die benötigten Funktionen implementieren">
        Öffne die umbenannte Datei und passe sie an die Events des Drittanbieter-Scripts an, das du integrierst:

        ```lua
        local moduleType = "stash"
        local moduleName = "yourModuleName"

        Integrations.modules = Integrations.modules or {}
        Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
        Integrations[moduleType] = Integrations[moduleType] or {}
        Integrations[moduleType][moduleName] = {}
        table.insert(Integrations.modules[moduleType], moduleName)

        -- Öffnet die Stash-UI für den angegebenen Marker
        Integrations[moduleType][moduleName].open = function(type, markerId)
            -- Füge hier deinen Code ein
        end
        ```
      </Step>
    </Steps>
  </Tab>

  <Tab title="Text UI">
    <Steps>
      <Step title="Zum Modules-Ordner navigieren">
        Gehe zum Ordner `jobs_creator/_modules/textui`.
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
