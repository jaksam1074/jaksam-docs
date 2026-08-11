---
title: "Missionsvorlage abrufen"
description: "Rufe die Daten einer Missionsvorlage client-seitig ab, z.B. Optionen, Bezeichnung oder Beschreibung."
icon: "clipboard-list"
---

Export, um eine Missionsvorlage client-seitig abzurufen, falls du ihre Daten benötigst — zum Beispiel Optionen, Bezeichnung, Beschreibung, usw.

Ein gutes Anwendungsbeispiel ist ein eigenes Menü, das nur eine begrenzte Anzahl an Missionen anzeigt, wobei Bezeichnung und Beschreibung mit diesem Export dargestellt werden.

Wenn du eine Mission nach der Auswahl manuell starten möchtest, kannst du dafür den [`startMission`-Export](/de/missions-creator/server/start-mission) nutzen.

```lua Export: getMissionTemplate
exports["missions_creator"]:getMissionTemplate(templateId)
```

#### Parameter

| Name         | Datentyp | Beschreibung             |
| ------------ | --------- | -------------------------- |
| `templateId` | integer   | Die ID der Missionsvorlage    |

#### Rückgabewert

| Name           | Datentyp | Beschreibung                                       |
| -------------- | --------- | ---------------------------------------------------- |
| `templateData` | table     | Die Daten der Missionsvorlage. Siehe Haupt-Keys unten       |

##### Haupt-Keys von `templateData`

| Key           | Typ     | Beschreibung                                 |
| ------------- | -------- | -------------------------------------------- |
| `id`          | integer  | Die ID der Missionsvorlage                       |
| `label`       | string   | Name/Bezeichnung der Mission                        |
| `description` | string   | Beschreibung der Mission                       |
| `options`     | table    | Table mit Missionsoptionen (siehe unten)         |

<Note>
  Die `options`-Table enthält üblicherweise Felder wie `startCoordinates`, `minPlayers`, `maxPlayers`, `allowedJobs`, `canBeRepeated`, `requiredMissions`.
</Note>
