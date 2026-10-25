---
title: "Fixer"
description: "Fixer in Boosting Creator: Käufer mit Namen, die Aufträge per E-Mail schicken, ein Auto ohne Kratzer, eine Umlackierung oder Tuning verlangen und mehr zahlen, je mehr sie dem Dieb vertrauen."
icon: "envelope"
---

Ein **Fixer** ist ein Käufer mit Namen. Statt eines anonymen Angebots bekommt der Spieler eine E-Mail von ihm auf den Laptop, und nach dem Job eine Antwort im **Posteingang**. Fixer sind standardmäßig aktiv und werden im Tab **Fixer** von `/boostingcreator` eingerichtet.

## Fixer-Einstellungen

| Feld | Was es macht |
| --- | --- |
| **Name für die Diebe**, **Initialen**, **Farbe** | Wie der Fixer in den E-Mails erscheint. |
| **Gekaufte Klassen** | Die Klassen, die der Fixer kauft. |
| **Ruf, bevor er einem Dieb schreibt** | Der Fixer schreibt nur Spielern mit diesem Ruf. |
| **Wunsch-Chance** | Wie oft der Fixer etwas mehr verlangt. |
| **Wünsche** | Bis zu 10, siehe unten. |
| **Nachrichten** | Die Angebots-E-Mail und die Antworten, wenn der Job gut lief, wenn ein Wunsch verfehlt wurde und wenn er gescheitert ist. |

Nachrichten können `{model}`, `{class}`, `{pay}`, `{colour}`, `{mods}`, `{condition}` und `{amount}` nutzen.

## Wünsche

Ein Wunsch ist eine zusätzliche Anforderung bei einem Übergabe-Auftrag:

| Typ | Das Auto muss |
| --- | --- |
| **Ohne Kratzer** | Mit mindestens einem bestimmten Zustand ankommen, zum Beispiel 95 %. |
| **Umlackierung** | In einer der gewählten Farben ankommen. Es spawnt in einer ganz anderen Farbe, muss also lackiert werden. |
| **Tuning beim Mechaniker** | Eine Anzahl Upgrades haben, aus Motor, Bremsen und Getriebe ab Stufe 2, Turbo und Xenon. |

Jeder Wunsch hat einen **Bonus** bei Erfüllung, einen **Abzug** bei Verfehlung, **Extra-Minuten** auf das Zeitlimit, das benötigte **Vertrauen** und die Zahl der **Mechaniker**, die online sein müssen (Jobs festgelegt unter **Einstellungen > Aufträge**). Während der Fahrt zeigt die Zielkarte, wie weit das Auto vom Wunsch entfernt ist, und wird grün, sobald er erfüllt ist.

## Vertrauen

Jeder Charakter hat bei jedem Fixer ein Vertrauen von 0 bis 100. Mehr Vertrauen erhöht die Bezahlung, standardmäßig um bis zu +20 % bei vollem Vertrauen, und schaltet die Wünsche frei, die es brauchen.

- Ein erledigter Job (mit erfülltem Wunsch oder ohne Wunsch) gibt Vertrauen.
- Ein verfehlter Wunsch kostet etwas Vertrauen.
- Ein gescheiterter oder abgelaufener Auftrag kostet mehr.

Die Werte werden unter **Einstellungen > Aufträge** festgelegt.

## Die Standard-Fixer

| Fixer | Kauft | Ab Ruf | Verlangt |
| --- | --- | --- | --- |
| Vinnie Russo | D bis B | 0 | ein Auto ohne Kratzer |
| Lola Navarro | C bis S | 60 | eine Umlackierung, mit einem Mechaniker online |
| Dmitri Volkov | B bis S | 200 | Tuning, und ein Auto in sehr gutem Zustand, sobald er dir vertraut |

<Info>
  Mit ausgeschalteten Fixern, oder wenn kein Fixer die Klasse kauft, ist das Angebot anonym und hat keinen Wunsch.
</Info>
