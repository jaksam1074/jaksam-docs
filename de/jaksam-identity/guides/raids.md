---
title: "Razzien"
description: "Lass Polizei-Jobs Fälscherwerkstätten aufbrechen, Beweismittel beschlagnahmen und versiegeln."
icon: "building-shield"
---

Beamte brechen die Tür einer Werkstatt auf, durchsuchen sie und versiegeln sie. Razzien werden in `Config.Raid` (`config/raid.lua`) oder auf der Razzien-Seite von `/documents config` eingestellt. `Config.Raid.enabled = false` schaltet sie ab.

## Einheiten

Ein oder mehrere Jobs, die zusammen stürmen, ab einem festgelegten Rang, mit einem Asservatenschrank an einem festgelegten Ort:

```lua
forces = {
    police = { label = 'LSPD', jobs = { 'police' }, minGrade = 0, locker = vec4(452.3, -980.0, 30.69, 90.0) },
},
```

<Warning>
  Platziere den Asservatenschrank jeder Einheit im Spiel (Razzien-Seite von `/documents config`). **Ohne Schrank kann nichts beschlagnahmt werden.**
</Warning>

## Ablauf einer Razzia

<Steps>
  <Step title="Die Tür aufbrechen">
    An der Tür einer Werkstatt, die einen Besitzer hat. Es braucht genug Beamte im Dienst online (`minOfficers`), das Item `door_ram` (`item`, `''` für keins) und Zeit: die Aufbruchzeit der Sicherheitsstufe der Werkstatt (30 Sekunden, 90 mit dem Upgrade). Der Beamte bleibt an der Tür: Weggehen oder Abbrechen stoppt es.
  </Step>
  <Step title="Die Warnung">
    Mit einer eingestellten Sicherheitswache wird jeder drinnen gewarnt und sieht den Countdown. Ohne Wache merkt drinnen niemand etwas. Mit dem Sicherheits-Upgrade bekommen die Mitglieder woanders einen Alarm.
  </Step>
  <Step title="Schreddern">
    Gewarnte Mitglieder vernichten während des Countdowns Beweise an den vier Schreddern: alle offenen Aufträge, oder was in einem Lager liegt. Die Arbeiter tun das auch: Auf der Personal-Seite des Laptops wählt der Boss, was sie vernichten, wenn die Wache Alarm schlägt, und sie teilen sich die Aufgaben. Was nicht erledigt ist, wenn die Tür nachgibt, bleibt.
  </Step>
  <Step title="Die offene Tür">
    Die Tür bleibt `openMinutes` lang offen. Beamte gehen hinein, die Arbeiter und die Wache heben die Hände, und keine Station, kein Computer und kein Laptop der Werkstatt nimmt eine Aktion an. An jedem Regal leert ein Beamter das Lager in den Asservatenschrank der Einheit. Am Boss-Laptop wird die Ausrüstung beschlagnahmt (`equipmentLoss`).
  </Step>
  <Step title="Versiegeln">
    Ein Beamter versiegelt die Werkstatt an ihrer Tür, oder die Zeit läuft ab. Jeder drinnen wird vor die Tür gesetzt, und `sealHours` lang kommt niemand vom besitzenden Job hinein. Die Arbeiter tun in der Zeit nichts und bekommen dafür keinen Lohn.
  </Step>
</Steps>

Eine Werkstatt kann `cooldownHours` nach dem letzten Aufbruch erneut aufgebrochen werden. Ein Siegel endet von selbst. Eine Werkstatt, die ihren Besitzer verliert, verliert ihr Siegel, und ein Neustart mitten in einer Razzia lässt die Werkstatt versiegelt.

## Konfiguration

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

## Admin-Befehle

| Befehl | Was |
| --- | --- |
| `/documents raid` | Razzien und Siegel auflisten |
| `/documents raid <workshop> end` | Eine laufende Razzia beenden |
| `/documents raid <workshop> unseal` | Ein Siegel aufheben |
| `/documents raid <workshop> reset` | Zusätzlich die Wartezeit bis zur nächsten Razzia löschen |

## Dispatch und Fortschrittsbalken

- `Editable.CanRaid` und `Editable.OnRaid` in `editable/server.lua`: eigene Bedingungen hinzufügen oder einen Dispatch-Ruf senden. Siehe [Darf stürmen](/de/jaksam-identity/server/hooks/can-raid) und [Bei Razzia](/de/jaksam-identity/server/hooks/on-raid).
- `Editable.Progress` in `editable/client.lua`: den Fortschrittsbalken ersetzen. Siehe [Fortschrittsbalken](/de/jaksam-identity/client/progress-bar).

Das Item `door_ram` steht in den drei Item-Dateien des install-Ordners, sein Bild in `install/images/`.
