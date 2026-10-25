---
title: "Orte"
description: "Jeder Ortstyp von Boosting Creator: Suchgebiete, Übergaben, VIN-Werkstätten, Chop Shops, Garagen mit ihrer Ausfahrt und dem Start des Autotransporters, Großabnehmer und Abschlepphöfe."
icon: "location-dot"
---

Alle Orte des Scripts werden im Tab **Orte** von `/boostingcreator` festgelegt. Jeder hat einen Namen, eine Position mit Ausrichtung und einen Radius. **Meine Position** füllt sie von dort aus, wo du stehst, oder vom Fahrzeug, in dem du sitzt, auf Bodenhöhe.

Im Zeilenmenü findest du **Teleport**, **Wegpunkt setzen** und, bei einem Suchgebiet, **Vorschau mit geparktem Fahrzeug** (ein durchsichtiges Auto erscheint 15 Sekunden lang an der Stelle).

## Ortstypen

| Typ | Was es ist | Radius |
| --- | --- | --- |
| **Suchgebiet** | Wo das Auftragsauto parkt. Die Position ist der genaue Parkplatz, der Radius ist der Kreis, den der Spieler absucht. | 30 bis 500 m |
| **Übergabe** | Der Käufer. Das Auto muss im Radius anhalten. | 2 bis 20 m |
| **VIN-Werkstatt** | Wohin ein VIN-Scratch-Auftrag das Auto bringt. | 2 bis 20 m |
| **Chop Shop** | Wohin ein Chop-Shop-Auftrag das Auto bringt. Er hat einen zweiten Punkt, den **Ablagepunkt der Teile**, zu dem der Dieb jedes Teil trägt. | 2 bis 20 m |
| **Garage** | Eine Garage, die Diebe kaufen können. Siehe [unten](#garagen). | 2 bis 20 m |
| **Großabnehmer** | Nimmt einen ganzen [Autotransporter](/de/boosting-creator/guides/garages-and-car-carrier#alles-auf-dem-autotransporter-verkaufen) ab. Braucht freie Fläche für einen Truck mit Anhänger. | 2 bis 20 m |
| **Abschlepphof** | Wohin Beamte einen beschlagnahmten Autotransporter bringen. | 2 bis 20 m |

Suchgebiete, Übergaben, VIN-Werkstätten und Chop Shops können über **Klassen, die ihn nutzen können** auf bestimmte Klassen beschränkt werden. Keine ausgewählt heißt: alle Klassen.

<Tip>
  Platziere ein Suchgebiet mit einem echten Auto: Setz dich hinein, innerhalb der Linien geparkt und in die Richtung, in die es zeigen soll, und drücke **Meine Position**. Das Auto des Auftrags erscheint genau dort.
</Tip>

## Ein Auftrag pro Ort

Ein Angebot reserviert sein Suchgebiet und seine Übergabe, bis der Auftrag endet, damit zwei Spieler nie gleichzeitig dasselbe Auto oder denselben Käufer bekommen. Wenn viele Spieler gleichzeitig boosten, füge mehr Orte hinzu: Eine Klasse ohne freies Suchgebiet oder freie Übergabe wird einfach nicht angeboten.

## Garagen

Eine Garage hat drei Punkte:

| Punkt | Wo er hin muss |
| --- | --- |
| **Eingang** | Zu Fuß am Garagentor. Hier kaufen Spieler die Garage und gehen hinein, und halten mit einem Auto im Radius an, um es abzustellen. |
| **Ausfahrt** | Wo ein aus der Garage geholtes Auto erscheint, mit dem Dieb am Steuer. Setz dich dort in ein geparktes Auto und drücke **Meine Position**. |
| **Start des Autotransporters** | Wo der Truck erscheint, wenn die ganze Garage verkauft wird. Der Anhänger erscheint 11 m gerade dahinter, lass also Platz. Setz dich dort in ein Fahrzeug, Blick zur Straße, und drücke **Meine Position**. |

Eine Garage hat außerdem einen **Preis**. Sie nutzt keine Klassen: Jeder Dieb kann sie kaufen.

<Warning>
  Eine Garage, die Spieler schon gekauft haben, kann nicht gelöscht werden. Nimm sie ihnen zuerst weg, im Tab **Spieler**.
</Warning>

<Frame>
  ![Garagen-Ort mit Eingang, Autoausgang und Start des Autotransporters](/images/boosting-creator/panel-garage.jpg)
</Frame>

## Die Standard-Orte

Das Script kommt mit 10 Suchgebieten, 5 Übergaben, 1 Chop Shop, 1 VIN-Werkstatt, 6 Garagen (Vespucci Beach, LSIA, Elysian Island, Sandy Shores, Grapeseed, Paleto Bay), 4 Großabnehmern und 1 Abschlepphof. Sie werden einmal hinzugefügt: Löschst du sie, kommen sie nicht zurück.
