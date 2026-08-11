---
title: "Tür aktualisieren"
description: "Aktualisiert server-seitig die Daten einer vorhandenen Tür."
icon: "pen"
---

```lua Export
exports["doors_creator"]:updateDoor(doorId, doorData)
```

### Parameter

| Name       | Datentyp | Beschreibung                     |
| ---------- | --------- | ----------------------------------- |
| `doorId`   | integer   | Die ID der zu aktualisierenden Tür           |
| `doorData` | table     | Die Türdaten, mit denen aktualisiert werden soll            |

### Format von doorData

Dieser Parameter kann alle Felder enthalten, die auch in `createDoor` genutzt werden. Du kannst nur die Felder angeben, die du aktualisieren möchtest — nicht angegebene Felder behalten ihre bestehenden Werte.

| Feld                        | Datentyp | Beschreibung                                            |
| ------------------------------ | --------- | -------------------------------------------------------- |
| `label`                          | string    | Name der Tür                                            |
| `defaultState`                   | integer   | Standardstatus: 1 = verriegelt, 0 = entriegelt                     |
| `doors`                           | table     | Array von Tür-Objekten mit Modell und Koordinaten             |
| `maxDistance`                     | number    | Maximale Entfernung für Interaktion                              |
| `iconCoords`                      | table     | Koordinaten, an denen das Interaktions-Symbol angezeigt wird                |
| `allowedJobs`                     | table     | Table mit zugriffsberechtigten Jobs, mit Rängen                  |
| `allowedGangs`                    | table     | Table mit zugriffsberechtigten Gangs, mit Rängen                 |
| `requiredItem`                    | string    | Für den Zugriff benötigtes Item                                       |
| `requiresJobAndItem`              | boolean   | Falls true, werden sowohl Job als auch Item benötigt                       |
| `requiredCode`                    | string    | Für den Zugriff benötigter Code                                       |
| `autoClosureSeconds`              | integer   | Sekunden, nach denen sich Türen automatisch schließen                          |
| `parentBuilding`                  | integer   | Gebäude-ID, zu der diese Tür gehört                               |
| `isSliding`                       | boolean   | Falls true, ist die Tür eine Schiebetür statt einer Drehtür                    |
| `displayIcon`                     | boolean   | Ob das Interaktions-Symbol angezeigt werden soll                        |
| `requiresIdentifier`              | boolean   | Falls true, sind bestimmte Identifier erlaubt                      |
| `allowedIdentifiers`              | table     | Table mit zugriffsberechtigten Identifiern                         |
| `vault`                            | table     | Konfiguration für Tresortüren                                       |
| `canBeLockpicked`                 | boolean   | Falls true, kann die Tür geknackt werden                             |
| `alertPoliceOnLockpick`           | boolean   | Falls true, wird die Polizei alarmiert, wenn die Tür geknackt wird           |
| `soundsData`                       | table     | Konfiguration eigener Sounds                                     |
| `requiredItemRemoveOnUse`         | boolean   | Falls true, wird das benötigte Item bei Nutzung entfernt               |

### Rückgabe

| Datentyp | Beschreibung                                      |
| --------- | ------------------------------------------------------ |
| boolean   | `true`, falls die Tür aktualisiert wurde, sonst `false`         |

## Beispiel

```lua
Citizen.CreateThread(function()
    local doorId = 55

    -- Beispiel 1: Nur bestimmte Eigenschaften aktualisieren
    local doorData = {
        -- Zugriffsberechtigungen aktualisieren
        allowedIdentifiers = {
            ["steam:1100001xxxxxxxx"] = true,
            ["license:xxxxxxxxxxxxxxx"] = true
        },
        allowedJobs = {
            ["police"] = {
                ["0"] = true,
                ["1"] = true,
                ["2"] = true
            }
        },

        -- Benötigtes Item aktualisieren
        requiredItem = "special_key",

        -- Lockpicking-Einstellungen ändern
        canBeLockpicked = true,
        alertPoliceOnLockpick = true
    }

    local success = exports["doors_creator"]:updateDoor(doorId, doorData)

    if success then
        print("Door with ID " .. doorId .. " has been updated")
    else
        print("Failed to update door with ID " .. doorId)
    end

    -- Beispiel 2: Vollständige Tür-Aktualisierung
    -- Dies würde alle Eigenschaften der Tür ersetzen
    local completeUpdate = {
        label = "Updated Door",
        defaultState = 0, -- Jetzt standardmäßig entriegelt
        doors = {
            {
                model = 747286790,
                coords = {
                    x = 152.7808,
                    y = -1000.5450,
                    z = 29.3962
                }
            }
        },
        maxDistance = 3.0, -- Erhöhte Interaktionsdistanz
        iconCoords = {
            x = 152.7808,
            y = -1000.5450,
            z = 29.3962
        },
        displayIcon = true,
        isSliding = false,
        parentBuilding = 2, -- Geänderte Gebäudezuordnung
        requiresJobAndItem = false
    }

    -- exports["doors_creator"]:updateDoor(doorId, completeUpdate)
end)
```
