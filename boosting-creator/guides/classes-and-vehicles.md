---
title: "Classes and vehicles"
description: "Create and tune Boosting Creator classes: reputation, pay, time limit, police, tracker, guards, crew chase, hotwire difficulty, VIN scratch and chop shop."
icon: "ranking-star"
---

A **class** is a tier of contracts. Five come with the script, D, C, B, A and S, and you can edit them or add your own in the **Classes** tab of `/boostingcreator`.

## Class settings

| Field | What it does |
| --- | --- |
| **ID** | Short code shown on the class chip. It can't be changed after the class is created. |
| **Name and colour** | How the class looks in the laptop, the HUD and the panel. |
| **Reputation to unlock** | A player gets offers of this class only from this reputation on. |
| **Reputation reward** | Given when the contract is done (delivered, VIN scratched or stored). |
| **Pay min / max** | The offer pay is random between the two. |
| **Time limit** | Minutes to finish the job, 5 to 240. |
| **Minimum police** | Offers of this class come only with this many officers online. |
| **Break-in call chance** | Chance that a witness calls the police when the car is broken into. |
| **GPS tracker** | On or off, and how many successful hacks remove it (1 to 10). |
| **Guards** | 1 to 6 armed guards around the parked car, difficulty 1 to 5. |
| **Crew chase** | 1 to 3 chasing cars, 1 to 3 gunmen besides the driver, difficulty 1 to 5. |
| **Hotwire** | Easy, Medium or Hard. Used only without vehicles_keys. |
| **VIN scratch allowed** | The class can come up as a VIN scratch contract (when VIN scratch is on in the settings). |
| **Chop shop allowed** | The class can come up as a chop shop contract (when the chop shop is on in the settings). |

<Info>
  Deleting a class also removes it from the fixers and locations that used it. Cars of that class already stored in a garage still sell.
</Info>

## The default classes

| Class | Reputation | Risks |
| --- | --- | --- |
| D | 0 | none, chop shop allowed |
| C | 60 | chop shop allowed |
| B | 200 | tracker, chop shop allowed |
| A | 500 | tracker, guards, VIN scratch allowed |
| S | 1000 | tracker, guards, crew chase, VIN scratch allowed |

## Vehicles

The **Vehicles** tab lists the cars of each class. A class can have up to 60 vehicles, and every offer picks one at random.

- **Add vehicles** opens a picker with every vanilla car and its picture.
- **Add by model name** adds an addon car by its spawn name. To give it a picture, put a `<spawn name>.webp` file in `boosting_creator/_vehicles_images/`, with the name spelled as you added it, and restart the script.

<Tip>
  A class with no vehicles never gets offered. The same goes for a class with no free search area or drop-off: see [Locations](/boosting-creator/guides/locations).
</Tip>
