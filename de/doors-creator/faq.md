---
title: "FAQ"
description: "Häufig gestellte Fragen speziell zu Doors Creator."
icon: "circle-question"
---

Diese Seite enthält FAQs, die **NUR** dieses Script betreffen — sieh dir auch die [allgemeinen FAQ](/de/jaksams-scripts/common-faq) für andere Probleme an.

<AccordionGroup>
  <Accordion title="Kann keine Tür auswählen">
    Falls du keine Tür auswählen kannst, bedeutet das, dass das Türmodell nicht in der erlaubten Türenliste ist.

    Um das Türmodell zur Liste hinzuzufügen, drücke **H** während du die Tür auswählst.

    Falls du die Tür nach Drücken von H immer noch nicht auswählen kannst, sind das die möglichen Gründe:

    - Du hast ein Script, das deinem Charakter eine Waffe hinzufügt
    - Die Tür ist aus irgendeinem Grund nicht nutzbar — bei einem modifizierten MLO ist das meist die Ursache
  </Accordion>

  <Accordion title="Tresortür funktioniert nicht">
    Falls eine bestimmte Tür mit der Tresor-Option nicht funktioniert, probiere **beide** Optionen, Verhältnis und Ausrichtung.

    Bei der Ausrichtung musst du selbst herausfinden, welcher Wert am besten zu dieser Tür passt (0-360 sind Min-/Max-Werte), oder den eingebauten Button im Script nutzen, um ihn zu finden.

    Probiere auch verschiedene Geschwindigkeiten (zum Beispiel langsamer).

    <Note>
      Falls eine Tür überhaupt nicht funktioniert, kann nichts dagegen getan werden.
    </Note>
  </Accordion>

  <Accordion title="Türen nach Neustart nicht gesperrt">
    Falls eine Tür nach einem Script-/Serverneustart nicht gesperrt ist, obwohl sie es sein sollte, hast du die Option zum Speichern des Türsperrzustands in den Menüeinstellungen des Scripts aktiviert.
  </Accordion>

  <Accordion title="Ich kann eine neue Tür nicht bestätigen">
    Falls du eine neue Tür nicht mit der ENTER-Taste bestätigen kannst, kannst du die Tastenbelegung in der Datei `integrations/cl_integrations.lua` bearbeiten.
  </Accordion>
</AccordionGroup>
