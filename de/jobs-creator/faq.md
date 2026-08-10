---
title: "FAQ"
description: "Häufig gestellte Fragen speziell zu Jobs Creator, zu Animationen, Gehältern, Outfits und häufigen Einrichtungsfehlern."
icon: "circle-question"
---

Diese Seite enthält FAQs, die **NUR** dieses Script betreffen. Sieh dir auch die [allgemeinen FAQ](/de/jaksams-scripts/common-faq) für andere Probleme an.

<AccordionGroup>
  <Accordion title="Wie man Animationen ändert">
    [Hier ist eine Liste verwendbarer Animationen](https://alexguirre.github.io/animations-list/)

    - Der größere Text ist das Animation-Dictionary
    - Der kleinere Text ist der Animationsname

    [Hier ist die Liste verwendbarer Szenarien](https://wiki.rage.mp/index.php?title=Scenarios)

    Der Hauptunterschied zwischen Szenarien und Animationen ist, dass ein Szenario meist ein Objekt hat, das an die Animation gebunden ist.

    _Externe Animationen können nicht verwendet werden._

    <Note>
      Nicht alle Animationen aus den Listen funktionieren.
    </Note>
  </Accordion>

  <Accordion title="Wie man Job-Fahrzeuge sperrt">
    Um Fahrzeuge zu sperren, hast du 2 Möglichkeiten:

    1. Nutze die Events und Exports aus der Script-Dokumentation, um dein eigenes Fahrzeugsperr-Script zu integrieren
    2. Nutze **jaksam's Vehicles Keys**, das eine eingebaute Jobs-Creator-Integration hat

    _Hinweis: Die Integration externer Scripts liegt komplett bei dir._
  </Accordion>

  <Accordion title="Wie verwaltet Jobs Creator Gehälter/Löhne?">
    Jobs Creator verwaltet keine Gehälter, das übernimmt das Framework-Script:

    - Bei ESX übernehmen `es_extended` und `esx_society` die Gehälter
    - Bei QBCore übernimmt `qb-core` die Gehälter

    Du kannst die Gehälter in Jobs Creator also **festlegen**, aber ausgezahlt werden sie vom Framework.
  </Accordion>

  <Accordion title='Fehler "Couldnt create marker" beheben'>
    Dieses Problem wird durch einen Fehler in der `job_data`-Tabelle der Datenbank verursacht.

    Mögliche Lösungen:

    1. Lösche die `job_data`-Tabelle aus der Datenbank und starte das Script/den Server neu
    2. Falls die `id`-Spalte der `job_data`-Tabelle nicht standardmäßig **AUTO INCREMENT** hat, setze den Standardwert dieser Spalte auf **AUTO INCREMENT**
  </Accordion>

  <Accordion title="Warum funktionieren die Outfit-Funktionen nicht?">
    Falls die Outfit-Funktionen nicht funktionieren, fehlen dir die benötigten Abhängigkeiten:

    - Bei ESX brauchst du die Scripts `esx_skin` und `skinchanger`
    - Bei QBCore brauchst du das Script `qb-clothing`

    Jobs Creator hat eine Integration für [**illenium-appearance**](https://github.com/iLLeniumStudios/illenium-appearance), das auf beiden Frameworks funktionieren sollte.
  </Accordion>

  <Accordion title="Waffen-Upgrader funktioniert nicht">
    Falls der Waffen-Upgrader-Marker nicht funktioniert, gibt es 2 mögliche Gründe:

    1. Du verwendest eine Addon-Waffe, hast sie aber nicht richtig in `es_extended` konfiguriert
    2. Dein Inventar verändert das Standardverhalten von **ESX/QBCore**, in diesem Fall musst du dein eigenes Inventar statt Jobs Creator für Waffenkomponenten und -farben verwenden
  </Accordion>

  <Accordion title="Fahrzeug-Beschriftungen in Garagen bearbeiten">
    Jobs Creator ruft Fahrzeug-Beschriftungen über FiveM-Natives ab, für eigene Beschriftungen musst du sie also in deinem Addon-Fahrzeug-Script konfigurieren.

    Es gibt mehrere Anleitungen in den FiveM-Foren dazu, wie man Anzeigenamen für Addon-Fahrzeuge konfiguriert.
  </Accordion>

  <Accordion title="QBCore erkennt Jobs-Creator-Jobs nicht">
    Normalerweise musst du keinen Code hinzufügen. Trotzdem kann eine abweichende Script-Startreihenfolge dazu führen, dass andere Scripts Jobs-Creator-Jobs nicht erkennen.

    **Wie kann ich das beheben?**

    Die Lösung ist sehr einfach: füge folgendes Event **client- und serverseitig** in dem Script hinzu, das die Jobs-Creator-Jobs nicht erkennt.

    ```lua
        -- jaksam's Jobs Creator Integration
        AddEventHandler('jobs_creator:injectJobs', function(jobs)
            -- Weise dem QBCore-Objekt die neuen Jobs zu, die folgende Zeile hängt von der Struktur deines Scripts ab
            QBCore.Shared.Jobs = jobs
        end)
    ```
  </Accordion>
</AccordionGroup>
