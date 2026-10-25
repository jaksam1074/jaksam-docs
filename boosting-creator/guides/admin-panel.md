---
title: "Admin panel"
description: "The Boosting Creator admin panel: live contracts, waiting players, player profiles, settings and Discord logs."
icon: "sliders"
---

Open the panel with `/boostingcreator` or `/boostcreator` (see [Admin permission](/boosting-creator/installation#admin-permission)). Every change applies at once, with no restart.

| Tab | What it's for |
| --- | --- |
| **Classes** | [Classes](/boosting-creator/guides/classes-and-vehicles) and their risks |
| **Vehicles** | The cars of each class |
| **Locations** | [Every place](/boosting-creator/guides/locations) of the script |
| **Fixers** | [Fixers](/boosting-creator/guides/fixers) and their demands |
| **Live** | Contracts running now and players waiting |
| **Players** | Profiles, reputation, history and garages |
| **Settings** | Everything else |

## Live

Refreshed every 5 seconds. For each contract running now: the player (and the crew members), the fixer and the demand, class, vehicle and plate, route, state with tracker, chase and carrier badges, and the time left. **Cancel** ends a contract with no reputation change.

**Players waiting** lists who is on a cooldown or at the daily limit, with the time left and a **Clear cooldown** button.

<Frame>
  ![Live tab with a running contract](/images/boosting-creator/panel-live.jpg)
</Frame>

## Players

Every boosting profile, online players first, searchable by name or identifier. Click one to open it:

- reputation, level, contracts done and failed, money earned
- **Set reputation** or **Add or remove reputation**
- the garage with its cars, and a button to remove a car
- the last 25 contracts with fixer, demand and the reason of the ending
- a danger menu: reset the profile, clear the history, take the garage back

## Settings

| Category | What's inside |
| --- | --- |
| **General** | Language, ACE permission, laptop item, account the pay goes to |
| **Contracts** | Offer timing, cooldowns and daily limit, reputation and pay, VIN scratch, chop shop, crews, fixers and trust, garages, bulk sale and seizure, guards, crew chase, break-in calls |
| **Theft** | Hotwire minigame, retry wait and alarm |
| **Tracker** | Pings, hacks and hack minigame |
| **Modules** | See [Modules](/boosting-creator/modules) |
| **Discord** | Logs and webhooks |

**Restore defaults** puts every setting back as it came with the script. Classes, locations and fixers are not touched.

## Discord logs

With Discord logs on, the script logs contract endings (with fixer and demand), cars that arrived too fast to be real, trackers disabled, VIN scratches, garages bought, carriers impounded, refused minigame results and every admin change. Everything goes to the main webhook.

To send a log type somewhere else, add it to `specificWebhooks` in `current_config.json`, with the types `contracts`, `vin`, `garages`, `admin` and `cheat`.
