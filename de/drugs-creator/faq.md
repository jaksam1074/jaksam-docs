---
title: "FAQ"
description: "Häufig gestellte Fragen speziell zu Drugs Creator."
icon: "circle-question"
---

Diese Seite enthält FAQs, die **NUR** dieses Script betreffen — sieh dir auch die [allgemeinen FAQ](/de/jaksams-scripts/common-faq) für andere Probleme an.

<AccordionGroup>
  <Accordion title="Drogen-Effekte funktionieren nicht">
    Falls die Effekte nicht funktionieren, funktioniert die `ESX.RegisterUsableItem`-Funktion deines `es_extended` nicht richtig.

    Du kannst Effekte trotzdem manuell registrieren/auslösen, über das Event [manually start drugs effects](/de/drugs-creator/client/manually-start-drugs-effects).

    Sowohl bei **ESX** als auch bei **QBCore** kann ein Anticheat die Drogen-Effekte stören.

    <Note>
      Das hängt nicht vom Script ab, wir können das für dich nicht lösen.
    </Note>
  </Accordion>

  <Accordion title="Schlechte Performance">
    Falls du serverseitige Performance-Probleme mit Drugs Creator hast, liegt es höchstwahrscheinlich am NPC-Verkauf, der alle Spieler-Inventare aktualisieren muss, um den Dialog `Press E to sell drugs` anzuzeigen.

    Um die Performance zu verbessern, aktiviere die entsprechende Option in den Ingame-Script-Einstellungen, damit der nächstgelegene NPC verwendet oder einer gespawnt wird (je nach Konfiguration).
  </Accordion>
</AccordionGroup>
