---
title: "Gebäude erstellen"
description: "Erstellt server-seitig ein neues Gebäude, um mehrere Türen unter gemeinsamen Zugriffsregeln zu gruppieren."
icon: "building"
---

```lua Export
exports["doors_creator"]:createBuilding(buildingData)
```

### Parameter

| Name           | Datentyp | Beschreibung                     |
| -------------- | --------- | ---------------------------------- |
| `buildingData` | table     | Die hinzuzufügenden Gebäudedaten       |

### Format von buildingData

| Feld                      | Datentyp | Beschreibung                                            | Erforderlich |
| --------------------------- | --------- | -------------------------------------------------------- | -------- |
| `label`                      | string    | Name des Gebäudes                                       | Ja      |
| `defaultState`               | integer   | Standardstatus: 1 = verriegelt, 0 = entriegelt                    | Ja      |
| `allowedJobs`                | table     | Table mit zugriffsberechtigten Jobs, mit Rängen                | Nein       |
| `allowedGangs`                | table     | Table mit zugriffsberechtigten Gangs, mit Rängen               | Nein       |
| `requiredItem`                | string    | Für den Zugriff benötigtes Item                                     | Nein       |
| `requiresJobAndItem`          | boolean   | Falls true, werden sowohl Job als auch Item benötigt                     | Nein       |
| `requiredCode`                | string    | Für den Zugriff benötigter Code                                     | Nein       |
| `autoClosureSeconds`          | integer   | Sekunden, nach denen sich Türen automatisch schließen                        | Nein       |
| `requiresIdentifier`          | boolean   | Falls true, sind bestimmte Identifier erlaubt                   | Nein       |
| `allowedIdentifiers`          | table     | Table mit zugriffsberechtigten Identifiern                      | Nein       |
| `requiredItemRemoveOnUse`     | boolean   | Falls true, wird das benötigte Item bei Nutzung entfernt           | Nein       |

### Rückgabe

| Datentyp | Beschreibung                                     |
| --------- | ---------------------------------------------------- |
| integer   | Die Gebäude-ID bei Erfolg, sonst `false`       |

## Beispiel

```lua
Citizen.CreateThread(function()
    local buildingData = {
        label = "Police Department",
        defaultState = 1, -- 1 = verriegelt, 0 = entriegelt

        -- Jobs, die dieses Gebäude betreten können
        allowedJobs = {
            ["police"] = {
                ["0"] = true, -- Recruit
                ["1"] = true, -- Officer
                ["2"] = true, -- Sergeant
                ["3"] = true  -- Lieutenant
            },
            ["sheriff"] = true
        },

        -- Gangs, die Zugriff haben (nur QB-Core)
        allowedGangs = {
            ["ballas"] = {
                ["3"] = true -- Nur Boss-Rang
            }
        },

        -- Für den Zugriff benötigtes Item
        requiredItem = "police_keycard",

        -- Falls true, benötigt der Spieler sowohl den Job ALS AUCH das Item
        requiresJobAndItem = true,

        -- Keypad-Code (falls zutreffend)
        requiredCode = "1234",

        -- Türen schließen sich nach dieser Anzahl Sekunden automatisch
        autoClosureSeconds = 5,

        -- Einzelne Spieler-Identifier, die Zugriff haben
        requiresIdentifier = true,
        allowedIdentifiers = {
            ["153vav3xxxxxxxxxxxxxxx"] = true,
            ["6ba2f3xxxxxxxxxxxxxxxx"] = true
        },

        -- Entfernt das Schlüssel-Item bei Nutzung
        requiredItemRemoveOnUse = false
    }

    local buildingId = exports["doors_creator"]:createBuilding(buildingData)

    if buildingId then
        print("Building created with ID: " .. buildingId)
    else
        print("Failed to create building")
    end
end)
```
