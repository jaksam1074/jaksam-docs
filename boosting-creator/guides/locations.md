---
title: "Locations"
description: "Every Boosting Creator location type: search areas, drop-offs, VIN body shops, chop shops, garages with their car exit and car carrier start, bulk buyers and impounds."
icon: "location-dot"
---

All the places of the script are set in the **Locations** tab of `/boostingcreator`. Each one has a name, a position with heading and a radius. **My position** fills them from where you stand, or from the vehicle you sit in, at ground level.

From the row menu you can **teleport** there, set a **waypoint**, or **preview** a search area (a see-through car appears at the spot for 15 seconds).

## Location types

| Type | What it is | Radius |
| --- | --- | --- |
| **Search area** | Where the contract car is parked. The position is the exact parking spot, the radius is the circle the player searches. | 30 to 500 m |
| **Drop-off** | The buyer. The car has to stop inside the radius. | 2 to 20 m |
| **VIN body shop** | Where a VIN scratch contract takes the car. | 2 to 20 m |
| **Chop shop** | Where a chop contract takes the car. It has a second point, the **parts drop point**, where the thief carries each part. | 2 to 20 m |
| **Garage** | A garage thieves can buy. See [below](#garages). | 2 to 20 m |
| **Bulk buyer** | Takes a whole [car carrier](/boosting-creator/guides/garages-and-car-carrier#selling-everything-on-the-car-carrier). Needs open ground for a truck with its trailer. | 2 to 20 m |
| **Impound** | Where officers bring a seized car carrier. | 2 to 20 m |

Search areas, drop-offs, VIN body shops and chop shops can be limited to some **classes**. None selected means every class.

<Tip>
  Place a search area with a real car: sit in it, parked inside the lines and facing the way it should face, and press **My position**. The car of the contract appears exactly there.
</Tip>

## One contract per spot

An offer reserves its search area and its drop-off until the contract ends, so two players never get the same car or the same buyer at once. With many players boosting at the same time, add more locations: a class with no free search area or drop-off is simply not offered.

## Garages

A garage has three points:

| Point | Where to put it |
| --- | --- |
| **Entrance** | On foot at the garage door. Players buy the garage and walk in here, and stop a car inside its radius to store it. |
| **Car exit** | Where a car taken out of the garage appears, with the thief at the wheel. Sit in a car parked there and press **My position**. |
| **Car carrier start** | Where the truck appears when the whole garage is sold. The trailer appears 11 m straight behind it, so leave room. Sit in a vehicle there, facing the road, and press **My position**. |

A garage also has a **price**. It doesn't use classes: any thief can buy it.

<Warning>
  A garage that players already bought can't be deleted. Take it back from them first, in the **Players** tab.
</Warning>

<Frame>
  ![Garage location with entrance, car exit and car carrier start](/images/boosting-creator/panel-garage.jpg)
</Frame>

## The default locations

The script comes with 10 search areas, 5 drop-offs, 1 chop shop, 1 VIN body shop, 6 garages (Vespucci Beach, LSIA, Elysian Island, Sandy Shores, Grapeseed, Paleto Bay), 4 bulk buyers and 1 impound. They are added once: if you delete them, they don't come back.
