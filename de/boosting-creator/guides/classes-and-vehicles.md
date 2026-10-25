---
title: "Klassen und Fahrzeuge"
description: "Klassen in Boosting Creator erstellen und einstellen: Ruf, Bezahlung, Zeitlimit, Polizei, Tracker, Wachen, Gang-Verfolgung, Schwierigkeit beim Kurzschließen, VIN-Scratch und Chop Shop."
icon: "ranking-star"
---

Eine **Klasse** ist eine Stufe von Aufträgen. Fünf sind beim Script dabei, D, C, B, A und S, und du kannst sie bearbeiten oder eigene hinzufügen, im Tab **Klassen** von `/boostingcreator`.

## Klasseneinstellungen

| Feld | Was es macht |
| --- | --- |
| **ID** | Kurzer Code, der auf dem Klassen-Chip steht. Er kann nach dem Erstellen der Klasse nicht mehr geändert werden. |
| **Name für die Spieler** und **Farbe** | Wie die Klasse im Laptop, im HUD und im Panel aussieht. |
| **Ruf zum Freischalten** | Ein Spieler bekommt Angebote dieser Klasse erst ab diesem Ruf. |
| **Ruf pro abgeschlossenem Auftrag** | Gibt es, wenn der Auftrag erledigt ist (geliefert, VIN abgeschliffen oder abgestellt). |
| **Mindestbezahlung** / **Höchstbezahlung** | Die Bezahlung des Angebots liegt zufällig zwischen beiden. |
| **Zeitlimit** | Minuten, um den Job zu erledigen, 5 bis 240. |
| **Benötigte Polizei im Dienst** | Angebote dieser Klasse kommen nur, wenn so viele Beamte online sind. |
| **Polizeiruf beim Aufbrechen** | Chance, dass ein Zeuge die Polizei ruft, wenn das Auto aufgebrochen wird. |
| **GPS-Tracker** | An oder aus, und wie viele erfolgreiche Hacks ihn entfernen (1 bis 10). |
| **Wachen am geparkten Fahrzeug** | 1 bis 6 bewaffnete Wachen um das geparkte Auto, Schwierigkeit 1 bis 5. |
| **Gang verfolgt das gestohlene Auto** | 1 bis 3 Verfolgerautos, 1 bis 3 Schützen neben dem Fahrer, Schwierigkeit 1 bis 5. |
| **Kurzschließen** | Leicht, Mittel oder Schwer. Wird nur ohne vehicles_keys genutzt. |
| **Kann ein VIN-Scratch-Auftrag sein** | Die Klasse kann als VIN-Scratch-Auftrag kommen (wenn VIN-Scratch in den Einstellungen aktiv ist). |
| **Kann ein Chop-Shop-Auftrag sein** | Die Klasse kann als Chop-Shop-Auftrag kommen (wenn der Chop Shop in den Einstellungen aktiv ist). |

<Info>
  Wird eine Klasse gelöscht, verschwindet sie auch bei den Fixern und Orten, die sie genutzt haben. Autos dieser Klasse, die schon in einer Garage stehen, lassen sich weiterhin verkaufen.
</Info>

## Die Standardklassen

| Klasse | Ruf | Risiken |
| --- | --- | --- |
| D | 0 | keine, Chop Shop erlaubt |
| C | 60 | Chop Shop erlaubt |
| B | 200 | Tracker, Chop Shop erlaubt |
| A | 500 | Tracker, Wachen, VIN-Scratch erlaubt |
| S | 1000 | Tracker, Wachen, Gang-Verfolgung, VIN-Scratch erlaubt |

## Fahrzeuge

Der Tab **Fahrzeuge** listet die Autos jeder Klasse. Eine Klasse kann bis zu 60 Fahrzeuge haben, und jedes Angebot wählt eines zufällig.

- **Fahrzeuge hinzufügen** öffnet eine Auswahl mit jedem Vanilla-Auto und seinem Bild.
- **Per Modellname hinzufügen** fügt ein Addon-Auto über seinen Spawnnamen hinzu. Für ein Bild leg eine Datei `<Spawnname>.webp` in `boosting_creator/_vehicles_images/`, mit dem Namen genau so geschrieben, wie du ihn hinzugefügt hast, und starte das Script neu.

<Tip>
  Eine Klasse ohne Fahrzeuge wird nie angeboten. Das gilt auch für eine Klasse ohne freies Suchgebiet oder freie Übergabe: siehe [Orte](/de/boosting-creator/guides/locations).
</Tip>
