---
title: "Start a mission"
description: "Manually start a mission server side, for example to integrate it with your own code."
icon: "play"
---

Export to manually start a mission server side, in case you want to integrate it with your code.

```lua Export: startMission
exports["missions_creator"]:startMission(templateId, playerIdOrArray)
```

#### Parameters

| Name               | Data Type       | Description                                        |
| ------------------ | --------------- | ----------------------------------------------------- |
| `templateId`        | integer         | The mission template ID                                |
| `playerIdOrArray`   | integer \| table | Player server ID, or an array of player server IDs      |

#### Return value

| Name         | Data Type | Description                                                              |
| ------------ | --------- | --------------------------------------------------------------------------- |
| `instanceId` | number    | The instance ID of the newly created mission, or `nil` if it could not be created |
