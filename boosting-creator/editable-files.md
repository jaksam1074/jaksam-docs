---
title: "Editable files"
description: "The Boosting Creator files meant to be edited: plate format, police jobs, debug, external event names, QBCore garage and the hooks."
icon: "file-pen"
---

Most of Boosting Creator is set up in game. A few things live in the `integrations/` folder instead, because they are code or because they rarely change.

<Warning>
  Keep a copy of these files before updating the script: an update can replace them.
</Warning>

## integrations/sh_integrations.lua

| Value | What it does |
| --- | --- |
| `EXAMPLE_PLATE` | Format of the contract plates. Letters and numbers are random, `#` marks the fixed part: `"#BST#123"` gives `BST920`, `BST945`... Max 8 characters. |
| `POLICE_JOBS_NAMES` | Jobs that count as [police](/boosting-creator/guides/police). |
| `SECONDS_TO_REFRESH_SHARED_OBJECT` | Refresh the framework object every X seconds, `nil` to never refresh. |
| `DEBUG_OUTPUTS` | Debug lines in the server console and F8. Also `setr boosting_creator_debug 1` in `server.cfg`, without editing the file. Turn it on when asking for support. |

## integrations/sv_integrations.lua

| Value | What it does |
| --- | --- |
| `EXTERNAL_EVENTS_NAMES` | Change only if your framework renamed its events and the script can't find them. |
| `VIN_SCRATCH_QB_GARAGE` | QBCore only: the garage a VIN scratched car is saved in, `pillboxgarage` by default. |
| `CanPlayerJoinBoostingQueue` | [Hook](/boosting-creator/server#canplayerjoinboostingqueue) to keep a player out of the queue. |
| `OnBoostingContractEnded` | [Hook](/boosting-creator/server#onboostingcontractended) called when a contract ends. |

## integrations/cl_integrations.lua

| Value | What it does |
| --- | --- |
| `DEFAULT_PROGRESSBAR_COLOR` | Colour of the default progress bar, a hex code. |
| `BLIP_TIME_AFTER_POLICE_ALERT` | Seconds the alert blip of the `default` dispatch module stays on the map, 120 by default. |
| `EXTERNAL_SCRIPTS_NAMES` | Folder names of `datacrack`, `utk_fingerprint` and `ultra-keypackhack`, if you renamed them. |

## current_config.json

The settings of the panel are saved in `boosting_creator/current_config.json`. Edit them from the panel. Two values have no field there:

- `specificWebhooks`: a Discord webhook per log type, see [Discord logs](/boosting-creator/guides/admin-panel#discord-logs)
- `minigamesMinSeconds`: the shortest time a minigame can take, see [Minigames](/boosting-creator/guides/minigames#add-your-own-minigame)

Stop the script before editing the file by hand, or the panel may save over your change.
