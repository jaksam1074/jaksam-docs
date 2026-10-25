---
title: "So läuft ein Auftrag ab"
description: "Die Spielerseite von Boosting Creator: der Laptop, die Warteschlange, Angebote, das Auto stehlen, der Tracker und die Arten, wie ein Auftrag enden kann."
icon: "route"
---

Diese Seite begleitet einen Auftrag vom Laptop bis zur Auszahlung, so wie der Spieler ihn erlebt.

## Der Laptop und die Warteschlange

Der Spieler benutzt das Item **Boosting Laptop** und drückt **Anstellen**. Die Warteschlange bleibt aktiv, auch wenn der Laptop zugeklappt ist: Ein kleiner Chip auf dem Bildschirm zeigt, wie lange er schon wartet.

- Polizei-Jobs können sich nicht anstellen (siehe [Polizei](/de/boosting-creator/guides/police)).
- Nach einem Auftrag kann es eine Wartezeit bis zum nächsten Angebot geben, und ein Tageslimit pro Charakter. Beides wird unter **Einstellungen > Aufträge** festgelegt und auf demselben Chip als Countdown angezeigt.

## Das Angebot

Alle 45 bis 120 Sekunden (standardmäßig) bekommt ein Spieler in der Warteschlange ein Angebot für eine Klasse, die er freigeschaltet hat, mit genug Polizei online und einem freien Platz, um das Auto zu spawnen. Höhere Klassen kommen häufiger, sobald sie freigeschaltet sind.

Das Angebot zeigt die Klasse, das Fahrzeug, die Bezahlung oder "Das Fahrzeug gehört dir", den Ruf, den es bringt, das Zeitlimit und die Risiken: Tracker, Wachen, Gang-Verfolgung, Schwierigkeit beim Kurzschließen. Es ist anonym, oder eine E-Mail von einem [Fixer](/de/boosting-creator/guides/fixers), der vielleicht etwas mehr verlangt. Der Spieler nimmt innerhalb von 60 Sekunden an oder lehnt ab.

Ist der Laptop zugeklappt, kommt das Angebot als Benachrichtigung mit einem Handy-Ton.

<Frame>
  ![Boosting-Laptop mit einem Auftragsangebot](/images/boosting-creator/laptop-offer.jpg)
</Frame>

## Das Auto finden

Ein gelber Kreis erscheint auf der Karte. Das Auto steht irgendwo darin, nie in der Mitte, und der Kreis wird um das Auto herum kleiner, je näher der Spieler kommt. Das Auto wird erst erstellt, wenn jemand in der Nähe ist, abgeschlossen und mit eigenem Kennzeichen. Bewaffnete Wachen können darum stehen.

<Frame>
  ![Zielkarte eines laufenden Auftrags](/images/boosting-creator/objective-card.jpg)
</Frame>

## Es stehlen

<Tabs>
  <Tab title="Ohne vehicles_keys">
    1. **Aufbrechen**: Zu Fuß neben dem Auto **E** drücken und den Skill Check bestehen. Jeder Versuch löst den Alarm aus und alarmiert die Wachen.
    2. **Kurzschließen**: Auf dem Fahrersitz **H** drücken und das Minispiel zum Kurzschließen spielen (standardmäßig die farbigen Kabel verbinden). Leicht, Mittel oder Schwer hängt von der Klasse ab. Ein Fehler erzeugt Funken, eine kurze Wartezeit und den Alarm.
  </Tab>
  <Tab title="Mit vehicles_keys">
    Der Spieler knackt das Schloss oder schlägt die Scheibe ein und schließt mit vehicles_keys kurz, wie bei jedem anderen Auto. Das gestohlene Auto bekommt temporäre Schlüssel, die am Ende des Auftrags entfernt werden.
  </Tab>
</Tabs>

Ein Aufbruch kann **gesehen** werden: Je nach Klasse ruft ein Zeuge ein paar Sekunden später die Polizei. Die Zielkarte sagt das dann.

## Entkommen

Sobald das Auto gestohlen ist:

- **GPS-Tracker** (Klassen mit Tracker): Die Polizei sieht alle paar Sekunden einen Kreis um das Auto. Beifahrer, oder der Fahrer im Stand, hacken ihn mit **J**, mehrmals hintereinander. Gelingt der letzte Hack, ist das Signal weg.
- **Gang-Verfolgung** (Klassen mit Verfolgung): Autos mit Schützen spawnen hinter dem Dieb. Sie endet, wenn sie zerstört oder abgehängt sind, oder nach ein paar Minuten.

Die Übergabe wird erst angezeigt, wenn der Tracker weg ist.

## Den Auftrag beenden

| Ende | Was passiert |
| --- | --- |
| **Übergabe** | Im grünen Marker anhalten und **E** drücken. Ein Käufer geht zum Auto, steigt ein und fährt weg. Die Bezahlung sinkt mit dem Schaden am Auto. |
| **VIN-Scratch** | In einer Karosseriewerkstatt zu Fuß **E** drücken: Nach 10 Sekunden gehört das Auto dem Spieler und ist in seiner Garage gespeichert. Kein Geld. |
| **Chop Shop** | Türen, Motorhaube, Kofferraum und Räder einzeln abbauen und jedes Teil zum Ablagepunkt tragen. Jedes Teil zahlt sofort seinen Anteil. |
| **Eigene Garage** | Bei einem einfachen Übergabe-Auftrag kann das Auto stattdessen in der [Garage](/de/boosting-creator/guides/garages-and-car-carrier) des Spielers abgestellt werden, um es später zu verkaufen. |

Ein Auftrag **scheitert**, wenn die Zeit abläuft, der Spieler stirbt, das Auto zerstört wird oder weg ist, oder der Spieler ihn über den Laptop abbricht. Ein gescheiterter oder abgelaufener Auftrag kostet etwas Ruf.

## Ruf

Jede Klasse gibt Ruf, wenn der Job erledigt ist. Ruf schaltet die nächsten Klassen frei und erhöht das Level, das im Laptop angezeigt wird. Der Laptop speichert außerdem den Verlauf der letzten Aufträge und die verdienten Summen.
