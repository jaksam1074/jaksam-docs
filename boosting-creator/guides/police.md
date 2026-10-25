---
title: "Police"
description: "What the police see and do in Boosting Creator: break-in calls, GPS tracker pings, dispatch modules, minimum police per class and car carrier seizures."
icon: "shield-halved"
---

## Police jobs

The jobs that count as police are listed in `integrations/sh_integrations.lua`:

```lua
POLICE_JOBS_NAMES = {
    ["police"] = true,
    ["sheriff"] = true,
}
```

Players with these jobs:

- receive the tracker pings and the break-in calls
- count for the **minimum police** of each class and of the car carrier
- can't join the boosting queue
- can seize a car carrier and bring it to an impound

## Break-in calls

When a contract car is broken into, the class **break-in call chance** decides if a witness calls the police. The call arrives after 10 seconds (by default, **Settings > Contracts > Police call on break-in > Head start before the call**) through the [dispatch module](/boosting-creator/modules). It is rolled once per contract, and works on classes without a tracker too.

## GPS tracker

On classes with a tracker, once the car is stolen every officer sees a red circle with a blip **Tracker \<plate\>** every 6 seconds, with a beep. The first ping also says the model and the plate.

The thieves hack the tracker with **J** (rebindable in the FiveM key bindings as "Boosting: hack the tracker"). Passengers can always hack, the driver only while stopped. Every successful hack makes the circle larger, every failed one sends a ping at once. When the last hack succeeds, the officers see **Tracker signal lost**.

| Setting (**Settings > Tracker**) | Default |
| --- | --- |
| Seconds between two pings to the police | 6 |
| Seconds between two hacks | 8 |
| Ping circle growth per hack | 60 m |
| The driver can hack when the vehicle is stopped | on |

With a dispatch module other than `default`, your dispatch also gets one call when the tracking starts.

## Car carrier

See [Garages and car carrier](/boosting-creator/guides/garages-and-car-carrier#police): a circle that follows the carrier, the seizure by getting in the driver seat, and the reward at the impound.
