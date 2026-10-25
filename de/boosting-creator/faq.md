---
title: "FAQ"
description: "Häufig gestellte Fragen speziell zu Boosting Creator: Angebote, die nie kommen, Autos, die nicht spawnen, das Laptop-Item, Tracker, vehicles_keys und Garagen."
icon: "circle-question"
---

Diese Seite enthält FAQs, die **NUR** dieses Script betreffen. Sieh dir auch die [allgemeinen FAQ](/de/jaksams-scripts/common-faq) für andere Probleme an.

<AccordionGroup>
  <Accordion title="Ich bin in der Warteschlange, aber es kommt nie ein Angebot">
    Ein Angebot braucht eine Klasse, die der Spieler freigeschaltet hat und die außerdem Folgendes hat:

    - mindestens ein Fahrzeug
    - genug Polizei online (**Benötigte Polizei im Dienst** der Klasse)
    - ein freies Suchgebiet und eine freie Übergabe für diese Klasse

    Mit den Standardwerten kommt das erste Angebot nach 45 bis 120 Sekunden. Sieh im Tab **Live** nach: Ein Spieler mit Cooldown oder am Tageslimit steht unter **Spieler, die auf ihren nächsten Auftrag warten**.
  </Accordion>

  <Accordion title="Der Auftrag wird abgebrochen, wenn ich mich dem Auto nähere">
    Das Auto wird vom Spiel des Spielers erstellt und vom Server geprüft. Meldet die Server-Konsole `wasn't created, is the model valid?`:

    - das Modell der Klasse ist falsch, oder ein Addon-Auto wird nicht gestreamt
    - `sv_entityLockdown` steht auf `strict`, Spieler können also keine Entities erstellen
  </Accordion>

  <Accordion title="Den Laptop zu benutzen tut nichts">
    Das Item existiert wahrscheinlich nicht in deinem Inventar: Die Server-Konsole meldet das beim Start in Gelb. Lege es an, wie unter [Laptop-Item anlegen](/de/boosting-creator/installation#laptop-item-anlegen) beschrieben. Hast du das Item in den Einstellungen umbenannt, starte das Script neu.
  </Accordion>

  <Accordion title="Polizisten können sich nicht anstellen">
    Das ist so gewollt: Die Jobs in `POLICE_JOBS_NAMES` können nicht boosten. Siehe [Polizei](/de/boosting-creator/guides/police).
  </Accordion>

  <Accordion title="Die Polizei sieht den Tracker nicht">
    Pings gehen nur an die Jobs in `POLICE_JOBS_NAMES` (`integrations/sh_integrations.lua`). Trage dort die Namen deiner Polizei-Jobs ein und starte das Script neu.
  </Accordion>

  <Accordion title="Die Minispiele zum Aufbrechen und Kurzschließen erscheinen nicht">
    Läuft `vehicles_keys`, wird das Auto mit vehicles_keys geknackt und kurzgeschlossen, und das eigene Aufbrechen und Kurzschließen des Scripts wird nicht genutzt. Das ist so gewollt.
  </Accordion>

  <Accordion title="Warum kann ich dieses Auto nicht in meiner Garage abstellen?">
    Nur einfache Übergabe-Aufträge können abgestellt werden: keine VIN-Scratch- oder Chop-Shop-Aufträge, keine Autos, für die ein Fixer einen Wunsch hat, und nicht, wenn die Garage schon 6 Autos hat.
  </Accordion>

  <Accordion title="Der Autotransporter kann nicht starten">
    Das Panel in der Garage sagt, warum. Er braucht mindestens so viele Autos wie unter **Benötigte Autos für den Komplettverkauf** eingestellt, genug Polizei im Dienst und einen freien Großabnehmer, der (standardmäßig) mindestens 2.500 m von der Garage entfernt ist.
  </Accordion>

  <Accordion title="Ich kann eine Garage nicht löschen">
    Spieler besitzen sie. Nimm sie zuerst jedem von ihnen im Tab **Spieler** weg.
  </Accordion>

  <Accordion title="Die Lieferung wurde als zu schnell abgelehnt">
    Ein Auto, das schneller ankommt als jede echte Fahrt (zum Beispiel nach einem Teleport), wird abgelehnt, und der Versuch wird auf Discord geloggt.
  </Accordion>
</AccordionGroup>
