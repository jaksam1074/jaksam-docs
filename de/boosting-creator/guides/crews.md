---
title: "Crews"
description: "Mit einer Crew boosten in Boosting Creator: Der Anführer lädt Spieler in der Nähe über den Laptop ein, die Crew teilt sich jeden Auftrag, die Bezahlung wird mit einem Bonus aufgeteilt."
icon: "users"
---

Spieler können zusammen boosten. Eine **Crew** ist ein Anführer plus die Spieler, die seine Einladung angenommen haben: Sie stellt sich als eine Einheit an und teilt sich jeden Auftrag, den der Anführer annimmt.

## Eine Crew bilden

1. Der Anführer öffnet den Laptop und geht zum Tab **Crew**. Spieler im Umkreis von 10 m erscheinen in der Liste.
2. Der Anführer lädt sie ein. Die Einladung gilt 60 Sekunden.
3. Der eingeladene Spieler nimmt über seinen eigenen Laptop an. Ab jetzt stellt sich der Anführer für ihn an.

Der Anführer kann nicht einladen, solange ein Auftrag läuft. Die Crew endet, wenn der Anführer sie auflöst oder sie verlässt.

## Während eines Auftrags

Jedes Mitglied kann das Auto stehlen, fahren, den Tracker hacken, es abliefern und in einem Chop Shop ausschlachten. Die Zielkarte und die Karte sind für alle gleich.

Die Angebote richten sich nach dem Ruf des Anführers.

Mit **Größere Crews, mehr Gegner** aktiv bekommt eine größere Crew mehr Gegner: eine Wache mehr für jedes Mitglied ab dem zweiten (bis 6) und ein Verfolgerauto mehr ab 3 Mitgliedern (bis 3), bei Klassen, die sie haben.

## Bezahlung und Ruf

Die Bezahlung wächst mit der Crew und wird zu gleichen Teilen aufgeteilt:

```text
total = pay × (1 + bonus % × (members − 1))
share = total ÷ members
```

Mit dem Standardbonus von 50 % zahlt ein Auftrag über 10.000, den 2 Spieler erledigen, insgesamt 15.000, also 7.500 pro Kopf. Das Angebot zeigt den Anteil jedes Mitglieds.

Jedes Mitglied bekommt den Ruf der Klasse, den Auftrag in seinem Verlauf und seine eigene Wartezeit bis zum nächsten Auftrag.

## Einstellungen

Unter **Einstellungen > Aufträge**, Abschnitt **Crew**:

| Einstellung | Standard |
| --- | --- |
| Crews | an. Aus: Der Laptop hat keinen Crew-Tab und jeder boostet allein |
| Maximale Crewgröße, Anführer inklusive | 4 Spieler (2 bis 4) |
| Mehr Bezahlung pro Mitglied ab dem zweiten | 50 % |
| Größere Crews, mehr Gegner | an |

Der Tab **Live** des Panels listet die Mitglieder jedes Crew-Auftrags.
