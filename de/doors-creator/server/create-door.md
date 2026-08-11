---
title: "Tür erstellen"
description: "Erstellt server-seitig eine neue Tür mit voller Kontrolle über Zugriffsregeln und Verhalten."
icon: "square-plus"
---

```lua Export
exports["doors_creator"]:createDoor(doorData)
```

### Parameter

| Name       | Datentyp | Beschreibung                  |
| ---------- | --------- | ---------------------------- |
| `doorData` | table     | Die hinzuzufügenden Türdaten     |

### Format von doorData

| Feld                        | Datentyp | Beschreibung                                            | Erforderlich |
| ------------------------------ | --------- | -------------------------------------------------------- | -------- |
| `label`                         | string    | Name der Tür                                            | Ja      |
| `defaultState`                  | integer   | Standardstatus: 1 = verriegelt, 0 = entriegelt                     | Ja      |
| `doors`                          | table     | Array von Tür-Objekten mit Modell und Koordinaten             | Ja      |
| `maxDistance`                    | number    | Maximale Entfernung für Interaktion                              | Ja      |
| `iconCoords`                     | table     | Koordinaten, an denen das Interaktions-Symbol angezeigt wird                | Ja      |
| `allowedJobs`                    | table     | Table mit zugriffsberechtigten Jobs, mit Rängen                  | Nein       |
| `allowedGangs`                   | table     | Table mit zugriffsberechtigten Gangs, mit Rängen                 | Nein       |
| `requiredItem`                   | string    | Für den Zugriff benötigtes Item                                       | Nein       |
| `requiresJobAndItem`             | boolean   | Falls true, werden sowohl Job als auch Item benötigt                       | Nein       |
| `requiredCode`                   | string    | Für den Zugriff benötigter Code                                       | Nein       |
| `autoClosureSeconds`             | integer   | Sekunden, nach denen sich Türen automatisch schließen                          | Nein       |
| `parentBuilding`                 | integer   | Gebäude-ID, zu der diese Tür gehört                               | Nein       |
| `isSliding`                      | boolean   | Falls true, ist die Tür eine Schiebetür statt einer Drehtür                    | Nein       |
| `displayIcon`                    | boolean   | Ob das Interaktions-Symbol angezeigt werden soll                        | Nein       |
| `requiresIdentifier`             | boolean   | Falls true, sind bestimmte Identifier erlaubt                      | Nein       |
| `allowedIdentifiers`             | table     | Table mit zugriffsberechtigten Identifiern                         | Nein       |
| `vault`                           | table     | Konfiguration für Tresortüren                                       | Nein       |
| `canBeLockpicked`                | boolean   | Falls true, kann die Tür geknackt werden                             | Nein       |
| `alertPoliceOnLockpick`          | boolean   | Falls true, wird die Polizei alarmiert, wenn die Tür geknackt wird           | Nein       |
| `soundsData`                      | table     | Konfiguration eigener Sounds                                     | Nein       |
| `requiredItemRemoveOnUse`        | boolean   | Falls true, wird das benötigte Item bei Nutzung entfernt               | Nein       |

### Rückgabe

| Datentyp | Beschreibung                                    |
| --------- | --------------------------------------------------- |
| boolean   | `true`, falls die Tür hinzugefügt wurde, sonst `false`       |

## Beispiel

```lua
Citizen.CreateThread(function()
    local doorData = {
        label = "Police Front Door",
        defaultState = 1, -- 1 = verriegelt, 0 = entriegelt

        -- Array physischer Tür-Objekte
        doors = {
            {
                model = 747286790, -- Hash des Tür-Modells
                coords = {
                    x = 152.7808,
                    y = -1000.5450,
                    z = 29.3962
                }
            },
            -- Du kannst eine zweite Tür für Doppeltüren hinzufügen
            {
                model = 747286791,
                coords = {
                    x = 154.8200,
                    y = -1000.5450,
                    z = 29.3962
                }
            }
        },

        -- Maximale Entfernung für Interaktion
        maxDistance = 2.0,

        -- Wo das Interaktions-Symbol angezeigt wird
        iconCoords = {
            x = 153.7808,
            y = -1000.5450,
            z = 29.3962
        },

        -- Jobs, die diese Tür nutzen können
        allowedJobs = {
            ["police"] = {
                ["0"] = true, -- Recruit
                ["1"] = true, -- Officer
                ["2"] = true  -- Sergeant
            },

            ["ambulance"] = true
        },

        -- Gangs, die Zugriff haben (nur QB-Core)
        allowedGangs = {
            ["ballas"] = {
                ["2"] = true, -- Nur höhere Ränge
                ["3"] = true
            }
        },

        -- Für den Zugriff benötigtes Item
        requiredItem = "police_keycard",

        -- Falls true, benötigt der Spieler sowohl den Job ALS AUCH das Item
        requiresJobAndItem = false,

        -- Gebäude, zu dem diese Tür gehört
        parentBuilding = 1,

        -- Ob es eine Schiebetür ist
        isSliding = false,

        -- Ob das Interaktions-Symbol angezeigt werden soll
        displayIcon = true,

        -- Tür kann geknackt werden
        canBeLockpicked = true,

        -- Polizei alarmieren, wenn geknackt
        alertPoliceOnLockpick = true,

        -- Eigene Sounds
        soundsData = {
            lockSound = "fence",
            unlockSound = "fence"
        }
    }

    local success = exports["doors_creator"]:createDoor(doorData)

    if success then
        print("Door created successfully")
    else
        print("Failed to create door")
    end
end)
```
