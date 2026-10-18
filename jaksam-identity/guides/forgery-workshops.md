---
title: "Forgery workshops"
description: "Add forgery workshops, let jobs buy and sell them, and configure upgrades, storages and who can enter."
icon: "warehouse"
---

A workshop is a door somewhere in the world that leads into its own copy of the forgery room (the biker fake ID interior from `bob74_ipl`). It belongs to one job or to nobody.

<Warning>
  **No workshop is configured out of the box.** The whole forgery side stays invisible until you add one in `config/forgery.lua` or in game with `/documents config`.
</Warning>

## Add a workshop

In `Config.Forgery.workshops` (`config/forgery.lua`):

```lua
workshops = {
    docks = { label = 'Docks', entrance = vec4(0.0, 0.0, 0.0, 0.0), price = 150000, jobs = {}, minGrade = 0 },
    east_side = { label = 'East side', entrance = vec4(0.0, 0.0, 0.0, 0.0), price = 90000, jobs = { 'vagos', 'ballas' }, minGrade = 1 },
},
```

| Field | Description |
| --- | --- |
| `label` | Name of the workshop |
| `entrance` | The door outside, a `vec4` with the heading for the way out |
| `price` | What a job pays to buy it |
| `jobs` | The jobs that may own it, `{}` for every job |
| `minGrade` | Lowest rank of the owning job that may enter |
| `owner` | Optional: the job it belongs to from the first start |

<Tip>
  It's easier in game: on the workshop page of `/documents config` press **Place**, walk to the door and click. Admins also add and remove workshops there while the server runs, and give a workshop to a job or take it away.
</Tip>

## Buying and owning

- **Buying:** a workshop without an owner shows "Workshop for sale" at its door. The boss of a job buys it for the job with black money (`Config.Forgery.payAccount`).
- **Several per job:** a job can own as many as it can pay, or as many as `ownership.perJob` allows.
- **Who is the boss:** the highest rank of the owning job, and as many ranks below it as `ownership.bossDepth` says. The boss buys, sells, hires and upgrades.
- **Members** of the owning job enter from the workshop's `minGrade`. Others ring the bell, and a member inside can let them in.
- **Selling:** the boss sells it at the workshop laptop (Upgrades page) and gets `ownership.refund` of what was paid back (nothing for a workshop an admin gave). `ownership.sellable = false` turns that off.

```lua
ownership = {
    perJob = 0,           -- workshops one job may own (0 = as many as it can pay)
    bossDepth = 0,        -- ranks below a job's highest that may buy, sell and manage too
    sellable = true,      -- the boss may sell the workshop at its laptop
    refund = 0.5,         -- share of what was paid that comes back when it is sold
    onRelease = 'room',   -- what stays when a workshop loses its owner
},
```

### What stays when a workshop loses its owner

| `onRelease` | Result |
| --- | --- |
| `room` | Upgrades and storages stay, workers are dismissed and open orders dropped |
| `all` | Everything stays for the next owner |
| `nothing` | An empty room |

<Info>
  **Black money:** on ESX the `black_money` account, on QBCore the `markedbills` item (its value in `metadata.worth`), on Qbox the stackable `black_money` item.
</Info>

## Upgrades

The boss buys upgrades at the laptop, with black money.

| Upgrade | What it changes |
| --- | --- |
| **Equipment** | The highest quality a forgery made here can reach (none, basic up to 70, pro up to 100), how many workers fit, and the embosser (pro only) |
| **Security** | How long officers need to break the door open (30 seconds, 90 with the upgrade), and an alarm to members elsewhere during a raid |
| **Style** | The look of the interior |

Prices are in `Config.Forgery.upgrades`, or in game.

## The boss laptop

The laptop on the boss desk shows its page on the real screen in the room, with tabs:

- **Overview:** workers, devices and desks
- **Staff:** hire and fire workers and the guard, pay wages, choose what the workers destroy during a raid
- **Tickets:** the order queue
- **Material:** order material, delivered to the raw material storage after a delay
- **Upgrades:** buy upgrades, sell the workshop

## Storages

Every workshop has three storages that open at their shelves:

| Storage | Content |
| --- | --- |
| Raw material | Blanks, toner and everything forging needs |
| Free | Free for the players |
| Results | Where the workers put the finished documents |

Sizes are in `Config.Forging.stores`. Workers put the documents of one order into an **ID stack** (`id_stack`), a container that holds them in one slot. Dragging one document onto another makes a stack too. qb-inventory has no containers, so there the documents arrive one by one.

<Note>
  Every target reaches 2 metres (`Config.TargetDistance`), and the server takes actions only from a member standing at the station. Guests and officers inside see none of the stations.
</Note>
