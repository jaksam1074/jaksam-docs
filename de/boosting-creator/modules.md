---
title: "Module"
description: "Ersetze Standard-Funktionen von Boosting Creator wie Dispatch, Fahrzeugschlüssel, Benachrichtigungen, Text-UI, Fortschrittsbalken und Skill Check durch deine eigenen Module."
icon: "puzzle-piece"
---

Module sind ein einfacher Weg, Boosting Creator mit den anderen Scripts deines Servers arbeiten zu lassen: Dispatch, Fahrzeugschlüssel, Benachrichtigungen und mehr.

Um ein vorhandenes Modul auszuwählen, öffne das `/boostingcreator`-Menü, gehe zu **Einstellungen > Module** und wähle es aus. So einfach ist das.

### Verfügbare Module

| Kategorie | Verfügbare Optionen |
| --- | --- |
| Polizei-Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Fahrzeugschlüssel | `none`, `qb-vehiclekeys`, `vehicles_keys` |
| Logs | `jaksam` |
| Benachrichtigungen | `default`, `ox_lib` |
| Fortschrittsbalken | `jaksam`, `ox_lib` |
| Skill Check | `jaksam`, `ox_lib` |
| Text-UI | `esx`, `none`, `ox_lib` |

<Info>
  **Fahrzeugschlüssel** gibt dem Dieb temporäre Schlüssel für das gestohlene Auto und nimmt sie zurück, wenn der Auftrag endet. Läuft `vehicles_keys`, wird das Auto außerdem mit vehicles_keys geknackt und kurzgeschlossen statt mit dem eigenen Aufbrechen und Kurzschließen des Scripts.
</Info>

### Ein eigenes Modul erstellen

<Steps>
  <Step title="Zum Modules-Ordner navigieren">
    Gehe zum Ordner `boosting_creator/_modules/<category>`, zum Beispiel `_modules/dispatch`.
  </Step>
  <Step title="Vorhandenes Modul duplizieren">
    Kopiere ein vorhandenes Modul (zum Beispiel `default`) und füge es im gleichen Ordner als Vorlage ein.
  </Step>
  <Step title="Die Kopie umbenennen">
    Benenne den Ordner und den `moduleName` in seinen Dateien passend zum Script um, das du integrierst.
  </Step>
  <Step title="Die Funktionen implementieren">
    Bearbeite die Funktionen so, dass sie dein Script aufrufen. Für einen Dispatch:

    ```lua
    local moduleType = "dispatch"
    local moduleName = "yourModuleName"

    -- Don't touch, required to appear in the in-game settings
    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Server side, once per alert
    Integrations[moduleType][moduleName].alertPoliceServerSide = function(coords, message, category)
        if not IsDuplicityVersion() then return end

        -- Call your dispatch script's export or event here
    end
    ```

    Die Funktionen, die jede Kategorie braucht:

    | Kategorie | Funktionen |
    | --- | --- |
    | Polizei-Dispatch | `alertPoliceServerSide`, `alertPoliceMemberClientSide` |
    | Fahrzeugschlüssel | `giveKeys`, `removeKeys` |
  </Step>
  <Step title="Neu starten und auswählen">
    Starte das Script neu und wähle dann dein Modul unter **Einstellungen > Module**.
  </Step>
</Steps>
