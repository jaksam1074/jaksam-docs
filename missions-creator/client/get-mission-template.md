---
title: "Get a mission template"
description: "Retrieve a mission template's data client side, such as its options, label, or description."
icon: "clipboard-list"
---

Export to get a mission template client side, in case you want to retrieve its data — for example options, label, description, etc.

A good example of usage is a custom menu that displays only a limited number of missions, showing their label and description using this export.

If you want to start a mission manually after selecting it, you can use the [`startMission` export](/missions-creator/server/start-mission) to do so.

```lua Export: getMissionTemplate
exports["missions_creator"]:getMissionTemplate(templateId)
```

#### Parameters

| Name         | Data Type | Description             |
| ------------ | --------- | -------------------------- |
| `templateId` | integer   | The mission template ID    |

#### Return value

| Name           | Data Type | Description                                       |
| -------------- | --------- | ---------------------------------------------------- |
| `templateData` | table     | The mission template data. See main keys below       |

##### Main keys of `templateData`

| Key           | Type     | Description                                 |
| ------------- | -------- | -------------------------------------------- |
| `id`          | integer  | The mission template ID                       |
| `label`       | string   | The mission name/label                        |
| `description` | string   | The mission description                       |
| `options`     | table    | Table with mission options (see below)         |

<Note>
  The `options` table usually contains fields like `startCoordinates`, `minPlayers`, `maxPlayers`, `allowedJobs`, `canBeRepeated`, `requiredMissions`.
</Note>
