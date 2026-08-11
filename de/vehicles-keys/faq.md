---
title: "FAQ"
description: "Häufig gestellte Fragen speziell zu Vehicles Keys."
icon: "circle-question"
---

Diese Seite enthält FAQs, die **NUR** dieses Script betreffen — sieh dir auch die [allgemeinen FAQ](/de/jaksams-scripts/common-faq) für andere Probleme an.

<AccordionGroup>
  <Accordion title="Hitch-Warnung / Performance">
    Falls dein Server Hitches/Performance-Probleme zeigt, liegt es daran, dass die Option `CONTINUOUSLY_REFRESH_PLAYERS_OWNED_VEHICLES` in `vehicles_keys/integrations/sv_integrations.lua` aktiviert ist.

    Wenn du die Option deaktivierst, verursacht sie keine Performance-Probleme mehr, du musst dann aber die Exports aus der Dokumentation nutzen, um die Fahrzeuge eines Spielers zu aktualisieren (zum Beispiel nachdem er ein neues Fahrzeug in einem Shop gekauft hat).

    Fertige **Beispiele** findest du auf der Seite [fix hotwiring bought car](/de/vehicles-keys/fix-hotwiring-bought-car).

    <Note>
      Die Integration mit externen Scripts liegt komplett bei dir.
    </Note>
  </Accordion>

  <Accordion title="Kann nicht ins Fahrzeug einsteigen">
    Falls du nach dem Zerstören der Fensterscheibe nicht mehr in ein Fahrzeug einsteigen kannst, läuft bei dir noch das Script `qb-vehicleskeys`.

    Entferne es, um das Problem zu lösen.
  </Accordion>
</AccordionGroup>
