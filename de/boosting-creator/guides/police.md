---
title: "Polizei"
description: "Was die Polizei in Boosting Creator sieht und tut: Polizeirufe beim Aufbrechen, Pings des GPS-Trackers, Dispatch-Module, Mindestanzahl Polizei pro Klasse und Beschlagnahme von Autotransportern."
icon: "shield-halved"
---

## Polizei-Jobs

Die Jobs, die als Polizei zählen, stehen in `integrations/sh_integrations.lua`:

```lua
POLICE_JOBS_NAMES = {
    ["police"] = true,
    ["sheriff"] = true,
}
```

Spieler mit diesen Jobs:

- bekommen die Tracker-Pings und die Polizeirufe beim Aufbrechen
- zählen für **Benötigte Polizei im Dienst** jeder Klasse und des Autotransporters
- können sich nicht in die Boosting-Warteschlange stellen
- können einen Autotransporter beschlagnahmen und zu einem Abschlepphof bringen

## Polizeirufe beim Aufbrechen

Wird ein Auftragsauto aufgebrochen, entscheidet der Wert **Polizeiruf beim Aufbrechen** der Klasse, ob ein Zeuge die Polizei ruft. Der Anruf kommt nach 10 Sekunden (standardmäßig, **Einstellungen > Aufträge > Polizeiruf beim Aufbrechen > Vorsprung vor dem Anruf**) über das [Dispatch-Modul](/de/boosting-creator/modules). Er wird einmal pro Auftrag gewürfelt und funktioniert auch bei Klassen ohne Tracker.

## GPS-Tracker

Bei Klassen mit Tracker sieht jeder Beamte, sobald das Auto gestohlen ist, alle 6 Sekunden einen roten Kreis mit einem Blip **Tracker \<Kennzeichen\>**, mit einem Piepton. Der erste Ping nennt auch Modell und Kennzeichen.

Die Diebe hacken den Tracker mit **J** (in den FiveM-Tastenbelegungen als "Boosting: Tracker hacken" änderbar). Beifahrer können immer hacken, der Fahrer nur im Stand. Jeder erfolgreiche Hack macht den Kreis größer, jeder misslungene schickt sofort einen Ping. Gelingt der letzte Hack, sehen die Beamten **Trackersignal verloren**.

| Einstellung (**Einstellungen > Tracker**) | Standard |
| --- | --- |
| Sekunden zwischen zwei Pings an die Polizei | 6 |
| Sekunden zwischen zwei Hacks | 8 |
| Wachstum des Ping-Kreises pro Hack | 60 m |
| Der Fahrer kann hacken, wenn das Fahrzeug steht | an |

Mit einem anderen Dispatch-Modul als `default` bekommt dein Dispatch außerdem einen Anruf, wenn die Ortung startet.

## Autotransporter

Siehe [Garagen und Autotransporter](/de/boosting-creator/guides/garages-and-car-carrier#polizei): ein Kreis, der dem Transporter folgt, die Beschlagnahme durch Einsteigen auf den Fahrersitz und die Belohnung am Abschlepphof.
