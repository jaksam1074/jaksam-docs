---
title: "Forging, workers and orders"
description: "How players forge documents by hand, how quality is decided, and how NPC workers and the order queue work."
icon: "print"
---

## Forging by hand

A forgery goes through the stations of the workshop, one ticket at a time:

<Steps>
  <Step title="Photo">
    At the backdrop: photograph yourself or another player, or call an NPC worker over with a camera. Pro equipment gives a transparent photo background.
  </Step>
  <Step title="Data entry">
    At a computer or laptop: type the name, date of birth and the other printed data.
  </Step>
  <Step title="Printing">
    Uses one blank and toner from the printer.
  </Step>
  <Step title="Laminating">
    At a laminating desk.
  </Step>
  <Step title="Embossing (optional)">
    Pro equipment only, adds quality.
  </Step>
  <Step title="Cutting">
    At the paper cutter: the document is finished.
  </Step>
</Steps>

Every station has a **skill check**: a success adds quality, a failure takes it (`Config.Forging.check`, and `Config.Forging.emboss` for the embosser). You can replace the minigame, see [Skill check](/jaksam-identity/client/skill-check).

### Copies

A player can copy a document they carry. Data and photo come from the source, and the fields can be changed: a real base with a false name. A copy of a forgery is capped at the source quality minus `Config.Forging.copyLoss`.

### Quality

The quality of a forgery (5 to 100) comes from:

- the **forger's level**: every forgery gives experience, and the level sets the quality base and what can be forged (identity first, then licences, then badges)
- the skill checks at the stations
- a little luck

It is then capped by the **equipment** of the workshop and by the **blank** used (`doc_blank` up to 60, `doc_blank_secure` up to 100).

```lua
levels = {
    { xp = 0,    base = 35, kinds = { identity = true } },
    { xp = 150,  base = 45, kinds = { identity = true, license = true } },
    { xp = 500,  base = 58, kinds = { identity = true, license = true } },
    { xp = 1200, base = 70, kinds = { identity = true, license = true, badge = true } },
    { xp = 2500, base = 82, kinds = { identity = true, license = true, badge = true } },
},
```

Quality decides which flaws show at a glance, in hand, under UV or only in the register. See [Forged documents and flaws](/jaksam-identity/guides/documents-and-register#forged-documents-and-flaws).

### Material

| Item | Use |
| --- | --- |
| `doc_blank` | Card blank, quality up to 60 |
| `doc_blank_secure` | Security blank, quality up to 100 |
| `printer_toner` | Toner cartridge, `Config.Forging.tonerCharges` prints each |
| `pvc_sheet` | Workers turn it into card blanks |
| `holo_foil` | Workers turn it with a blank into a security blank |

Material is ordered at a laptop with black money and delivered to the raw material storage after a delay (`Config.Forging.orders`).

## Orders

An order is a number of tickets of one document type and blank, which the workers and the players draw from (urgent first, then the oldest).

- **Priority:** low, normal or urgent
- **Assignee:** everyone, one player, or one worker
- **Pause, resume, cancel**
- **Fixed data:** an order made from a copy or one set of data repeats it on its tickets
- **Batches:** made-up identities with no photo, handed straight to the workers
- **Hand over:** a ticket can be given to the workers, or to one worker, and taken back

Each action needs a minimum job grade:

```lua
queue = {
    maxAmount = 50,            -- tickets per order
    maxOpenTickets = 300,      -- open tickets per workshop
    offlineMinutes = 10,       -- an order assigned to a player who stays away this long goes back to everyone
    rights = { create = 0, priority = 1, assign = 2, pause = 1, cancel = 2, handover = 0 },
},
```

## NPC workers

The boss hires workers at the laptop. They walk from device to device, take tickets through printer, laminating desk and cutter, refill the printers with toner and carry the finished documents into the results storage.

| Tier | Quality base | Speed | Fail chance | Tickets at once |
| --- | --- | --- | --- | --- |
| Rookie | 40 | 1.0 | 35% | 1 |
| Skilled | 60 | 1.3 | 20% | 3 |
| Pro | 78 | 1.6 | 10% | 5 |

- **Roles:** forging, or producing material (PVC to blanks, blank and foil to security blanks)
- **Worker cards:** at a worker you see the tier, a live status with a timer and bars for speed, failure rate, sheet size and cartridges. Give tasks directly: fetch toner, take an order or ticket, change role, fire
- **Wages:** the boss deposits black money and wages are taken once per period. An unpaid worker quits. Time spent sealed after a raid costs nothing
- **Guard:** one security guard per workshop warns everyone inside when officers start breaking the door open
- A worker's quality never exceeds the level base of the best player forger of the owning job
- The number of workers depends on the equipment upgrade

Hire prices, wages and working times are in `config/npc.lua`, or in game on the workers page of `/documents config`.

<Tip>
  `Config.Bridge.menu = 'ox_lib'` replaces the interaction cards at workers and stations with ox_lib context menus.
</Tip>

## Demo mode

For showcase videos and demo servers: the storages are always stocked, working times are short, nothing costs money and nobody fails. Turn it on with `Config.Demo = true` or `/documents demo on` (not kept after a restart).
