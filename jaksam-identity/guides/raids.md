---
title: "Raids"
description: "Let police jobs break forgery workshops open, seize evidence and seal them."
icon: "building-shield"
---

Officers break the door of a workshop open, search it and seal it. Raids are configured in `Config.Raid` (`config/raid.lua`) or on the Raids page of `/documents config`. `Config.Raid.enabled = false` turns them off.

## Forces

One or more jobs that raid together, from a rank you set, with an evidence locker at a place you set:

```lua
forces = {
    police = { label = 'LSPD', jobs = { 'police' }, minGrade = 0, locker = vec4(452.3, -980.0, 30.69, 90.0) },
},
```

<Warning>
  Place the evidence locker of each force in game (Raids page of `/documents config`). **Without a locker nothing can be seized.**
</Warning>

## How a raid goes

<Steps>
  <Step title="Breaking the door open">
    At the door of a workshop that has an owner. It needs enough officers on duty online (`minOfficers`), the item `door_ram` (`item`, `''` for none) and time: the breach time of the workshop's security level (30 seconds, 90 with the upgrade). The officer stays at the door: walking away or cancelling stops it.
  </Step>
  <Step title="The warning">
    With a security guard hired, everyone inside is warned and sees the countdown. Without one, nobody inside notices. With the security upgrade, the members elsewhere get an alarm.
  </Step>
  <Step title="Shredding">
    Warned members destroy evidence at the four shredders during the countdown: every open order, or what lies in one storage. The workers do it too: on the Staff page of the laptop the boss picks what they destroy when the guard raises the alarm, and they share the tasks. What is not done when the door gives way stays.
  </Step>
  <Step title="The open door">
    The door stays open for `openMinutes`. Officers enter, the workers and the guard put their hands up, and no station, computer or laptop of the workshop takes an action. At each shelf an officer empties the storage into the evidence locker of the force. At the boss laptop the equipment is seized (`equipmentLoss`).
  </Step>
  <Step title="Sealing">
    An officer seals the workshop at its door, or the time runs out. Everyone inside is put at the door, and for `sealHours` nobody of the owning job gets in. The workers do nothing meanwhile and are owed no wage for that time.
  </Step>
</Steps>

A workshop can be breached again `cooldownHours` after the last breach. A seal ends by itself. A workshop that loses its owner loses its seal, and a restart in the middle of a raid leaves the workshop sealed.

## Configuration

```lua
Config.Raid = {
    enabled = true,
    minOfficers = 2,            -- officers of all forces that must be online (0 = no minimum)
    dutyOnly = true,            -- only officers on duty count and act
    item = 'door_ram',          -- the item a breach needs ('' = none)
    consumeItem = true,         -- the item is used up when the door gives way
    warnNeedsGuard = true,      -- those inside are warned only when the workshop has a security guard
    alarmNeedsSecurity = true,  -- members elsewhere are alarmed only with the security upgrade
    openMinutes = 20,           -- the door stays open this long unless sealed earlier
    sealHours = 12,             -- nobody of the owning job gets in for this long (0 = no seal)
    cooldownHours = 24,         -- no new breach for this long after a breach
    retryMinutes = 5,           -- a breach given up can be tried again after this long
    equipmentLoss = 'level',    -- 'level' one level down | 'all' gone | 'nothing' cannot be seized
    seizeSeconds = 10,
    shredWhile = 'breach',      -- 'breach' only during the countdown | 'raid' until the raid is over
    shredSeconds = 8,
    workersShred = true,
    locker = { slots = 200, weight = 2000.0 },
}
```

## Admin commands

| Command | What |
| --- | --- |
| `/documents raid` | List the raids and seals |
| `/documents raid <workshop> end` | End a running raid |
| `/documents raid <workshop> unseal` | Lift a seal |
| `/documents raid <workshop> reset` | Also clear the wait until the next raid |

## Dispatch and progress bar

- `Editable.CanRaid` and `Editable.OnRaid` in `editable/server.lua`: add your own conditions, or send a dispatch call. See [Can raid](/jaksam-identity/server/hooks/can-raid) and [On raid](/jaksam-identity/server/hooks/on-raid).
- `Editable.Progress` in `editable/client.lua`: replace the progress bar. See [Progress bar](/jaksam-identity/client/progress-bar).

The `door_ram` item is in the three item files of the install folder, its image in `install/images/`.
