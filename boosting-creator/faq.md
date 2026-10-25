---
title: "FAQ"
description: "Frequently asked questions specific to Boosting Creator: offers that never come, cars that don't spawn, the laptop item, trackers, vehicles_keys and garages."
icon: "circle-question"
---

This page has FAQs related **ONLY to this script**. Be sure to also check the [common FAQ](/jaksams-scripts/common-faq) for other issues.

<AccordionGroup>
  <Accordion title="I'm in the queue but no offer ever comes">
    An offer needs a class the player unlocked that also has:

    - at least one vehicle
    - enough police online (the class **Minimum police**)
    - a free search area and a free drop-off for that class

    With the defaults the first offer comes after 45 to 120 seconds. Check the **Live** tab: a player on a cooldown or at the daily limit is listed under **Players waiting**.
  </Accordion>

  <Accordion title="The contract is cancelled when I get close to the car">
    The car is created by the player's game and checked by the server. If the server console says `wasn't created, is the model valid?`:

    - the model of the class is wrong, or an addon car isn't streamed
    - `sv_entityLockdown` is set to `strict`, so players can't create entities
  </Accordion>

  <Accordion title="Using the laptop does nothing">
    The item probably doesn't exist in your inventory: the server console says it at start, in yellow. Create it as shown in [Add the laptop item](/boosting-creator/installation#add-the-laptop-item). If you renamed the item in the settings, restart the script.
  </Accordion>

  <Accordion title="Police officers can't join the queue">
    That's intended: the jobs in `POLICE_JOBS_NAMES` can't boost. See [Police](/boosting-creator/guides/police).
  </Accordion>

  <Accordion title="The police don't see the tracker">
    Pings go only to the jobs in `POLICE_JOBS_NAMES` (`integrations/sh_integrations.lua`). Add your police job names there and restart the script.
  </Accordion>

  <Accordion title="The break-in and hotwire minigames don't show up">
    With `vehicles_keys` started, the car is lockpicked and hotwired with vehicles_keys, and the script's own break-in and hotwire are not used. That's intended.
  </Accordion>

  <Accordion title="Why can't I store this car in my garage?">
    Only plain drop-off contracts can be stored: not VIN scratch or chop shop contracts, not cars a fixer asked something for, and not when the garage already has 6 cars.
  </Accordion>

  <Accordion title="The car carrier can't start">
    The panel inside the garage says why. It needs at least the cars set in **Cars needed to sell all**, enough police on duty, and a free bulk buyer at least 2,500 m from the garage (by default).
  </Accordion>

  <Accordion title="I can't delete a garage">
    Players own it. Take it back from each of them in the **Players** tab first.
  </Accordion>

  <Accordion title="The delivery was refused as too fast">
    A car that arrives faster than any real drive (for example after a teleport) is refused, and the attempt is logged on Discord.
  </Accordion>
</AccordionGroup>
