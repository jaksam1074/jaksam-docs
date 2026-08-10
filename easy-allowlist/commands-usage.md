---
title: "Commands usage"
description: "Console and in-game commands for managing the allowlist and queue priority."
icon: "terminal"
---

All commands can be used either in-game by server admins or directly from the server console.

### Add allowlist

```
/add_allowlist identifier/requestId
```

The parameter can be either an identifier **or** a request ID.

| Parameter    | Type    | Description                                                                                                                        |
| ------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `identifier` | string  | The player's **main** identifier (can be the Steam hex, the Rockstar license, or the Discord ID). Use the identifier configured in the script settings. |
| `requestId`  | integer | The ID of the request. This is the ID shown to players after they send the allowlist request.                                       |

#### Example

```
/add_allowlist 7b1261c1ae07dr156af762fcb1bec11a403b9413
```

### Remove allowlist

```
/remove_allowlist identifier
```

The parameter **must** be the main identifier of the player.

| Parameter    | Type   | Description                                                                                                                        |
| ------------ | ------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `identifier` | string | The player's **main** identifier (can be the Steam hex, the Rockstar license, or the Discord ID). Use the identifier configured in the script settings. |

#### Example

```
/remove_allowlist 7b1261c1ae07dr156af762fcb1bec11a403b9413
```

### Set queue priority

```
/set_queue_priority identifier/playerId priority
```

The **first** parameter can be a main identifier **or** a player ID (if the player is online).

| Parameter    | Type    | Description                                                                                                                        |
| ------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `identifier` | string  | The player's **main** identifier (can be the Steam hex, the Rockstar license, or the Discord ID). Use the identifier configured in the script settings. |
| `playerId`   | integer | The server ID of the player.                                                                                                          |
| `priority`   | integer | The priority of the player. Higher number = more priority.                                                                            |

#### Example

```
/set_queue_priority 7b1261c1ae07dr156af762fcb1bec11a403b9413 15
```
