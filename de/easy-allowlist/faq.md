---
title: "FAQ"
description: "Häufig gestellte Fragen speziell zu Easy Allowlist & Queue."
icon: "circle-question"
---

Diese Seite enthält FAQs, die **NUR** dieses Script betreffen — sieh dir auch die [allgemeinen FAQ](/de/jaksams-scripts/common-faq) für andere Probleme an.

<AccordionGroup>
  <Accordion title="Wie füge ich mich selbst zur Allowlist hinzu">
    Das Script erkennt automatisch, wenn die Allowlist komplett leer ist, du wirst beim ersten Beitritt also automatisch gewhitelistet.

    Um manuell zu whitelisten, sende die Allowlist-Anfrage an deinen Server und nutze dann den Befehl `add_allowlist DeineRequestIdHier` in der Serverkonsole.
  </Accordion>

  <Accordion title='Hängt bei "deferring connection..."'>
    Falls beim Verbinden mit deinem Server `deferring connection...` angezeigt wird und ohne jeden Fehler hängen bleibt, versuch Folgendes:

    <Steps>
      <Step title="Deferrals-Datei öffnen">
        Öffne die Datei `easy_allowlist/server/deferrals.lua`.
      </Step>
      <Step title="Die Wartezeit finden">
        Suche nach dem Code `Citizen.Wait(500)`.
      </Step>
      <Step title="Die Wartezeit erhöhen">
        Ändere ihn von `Citizen.Wait(500)` zu `Citizen.Wait(10000)` oder höher, falls es weiterhin nicht funktioniert.
      </Step>
      <Step title="Speichern und neu starten">
        Speichere die Datei und starte das Script neu.
      </Step>
    </Steps>
  </Accordion>
</AccordionGroup>
