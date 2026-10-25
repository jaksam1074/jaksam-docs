---
title: "How a contract works"
description: "The player side of Boosting Creator: the laptop, the queue, offers, stealing the car, the tracker and the ways a contract can end."
icon: "route"
---

This page follows one contract from the laptop to the payout, as the player sees it.

## The laptop and the queue

The player uses the **boosting laptop** item and presses **Join queue**. The queue stays active after the laptop is closed: a small chip on screen shows how long they have been waiting.

- Police jobs can't join the queue (see [Police](/boosting-creator/guides/police)).
- After a contract there can be a wait before the next offer, and a daily limit per character. Both are set in **Settings > Contracts** and shown on the same chip as a countdown.

## The offer

Every 45 to 120 seconds (by default) a queued player gets an offer for a class they unlocked, with enough police online and a free spot to spawn the car. Higher classes come up more often once they are unlocked.

The offer shows the class, the vehicle, the pay or "the vehicle is yours", the reputation it gives, the time limit and the risks: tracker, guards, crew chase, hotwire difficulty. It is anonymous, or an email from a [fixer](/boosting-creator/guides/fixers) who may ask for something more. The player accepts or declines within 60 seconds.

If the laptop is closed, the offer arrives as a notification with a phone sound.

<Frame>
  ![Boosting laptop with a contract offer](/images/boosting-creator/laptop-offer.jpg)
</Frame>

## Finding the car

A yellow circle appears on the map. The car is somewhere inside it, never in the middle, and the circle shrinks around it as the player gets closer. The car is created only when someone is near, locked, with its own plate. Armed guards may stand around it.

<Frame>
  ![Objective card of an active contract](/images/boosting-creator/objective-card.jpg)
</Frame>

## Stealing it

<Tabs>
  <Tab title="Without vehicles_keys">
    1. **Break in**: on foot next to the car, press **E** and pass the skill check. Every attempt sets off the alarm and alerts the guards.
    2. **Hotwire**: in the driver seat press **H** and play the hotwire minigame (connect the coloured wires by default). Easy, Medium or Hard depends on the class. A mistake makes sparks, a short wait, and the alarm.
  </Tab>
  <Tab title="With vehicles_keys">
    The player lockpicks or breaks the glass and hotwires with vehicles_keys, as with any other car. The stolen car gets temporary keys, removed at the end of the contract.
  </Tab>
</Tabs>

A break-in can be **spotted**: depending on the class, a witness calls the police a few seconds later. The objective card then says so.

## Getting away

Once the car is stolen:

- **GPS tracker** (classes with it): the police see a circle around the car every few seconds. Passengers, or the driver while stopped, hack it with **J**, a few times in a row. When the last hack succeeds the signal is lost.
- **Crew chase** (classes with it): cars with gunmen spawn behind the thief. It ends when they are destroyed, left behind, or after a few minutes.

The drop-off is shown only once the tracker is gone.

## Ending the contract

| Ending | What happens |
| --- | --- |
| **Drop-off** | Stop inside the green marker and press **E**. A buyer walks to the car, gets in and drives away. The pay goes down with the car damage. |
| **VIN scratch** | At a body shop, on foot, press **E**: after 10 seconds the car is the player's, saved in their garage. No money. |
| **Chop shop** | Strip the doors, hood, trunk and wheels one by one and carry each part to the drop point. Every part pays its share at once. |
| **Own garage** | On a plain drop-off contract, the car can be stored in the player's [garage](/boosting-creator/guides/garages-and-car-carrier) instead, to sell later. |

A contract **fails** when the time runs out, the player dies, the car is destroyed or gone, or the player abandons it from the laptop. A failed or expired contract takes away some reputation.

## Reputation

Every class gives reputation when the job is done. Reputation unlocks the next classes and raises the level shown in the laptop. The laptop also keeps the history of the last contracts and the totals earned.
