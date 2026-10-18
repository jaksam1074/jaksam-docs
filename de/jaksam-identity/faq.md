---
title: "FAQ"
description: "Häufig gestellte Fragen speziell zu Jaksam Identity, zu Werkstätten, Razzien, Dokumenten, qb-inventory-Siegeln und Integrationen."
icon: "circle-question"
---

Diese Seite enthält FAQs, die **NUR** dieses Script betreffen. Sieh dir auch die [allgemeinen FAQ](/de/jaksams-scripts/common-faq) für andere Probleme an.

<AccordionGroup>
  <Accordion title="Ich finde keine Fälscherwerkstatt in der Welt">
    Ab Werk ist keine Werkstatt eingerichtet, die ganze Fälscherseite bleibt also unsichtbar, bis du eine hinzufügst.

    Füge sie in `Config.Forgery.workshops` (`config/forgery.lua`) hinzu, oder im Spiel auf der Werkstatt-Seite von `/documents config`. Siehe [Fälscherwerkstätten](/de/jaksam-identity/guides/forgery-workshops).
  </Accordion>

  <Accordion title="Der Innenraum der Werkstatt ist leer oder unsichtbar">
    Die Werkstatt nutzt den Biker-Fake-ID-Innenraum aus `bob74_ipl`. Stelle sicher, dass `bob74_ipl` installiert ist und **vor** `jksm_identity` startet. Fehlt es, nennt die Konsole es beim Start rot.
  </Accordion>

  <Accordion title="Beamte können bei einer Razzia nichts beschlagnahmen">
    Jede Einheit braucht einen Asservatenschrank. Platziere ihn auf der Razzien-Seite von `/documents config`, oder setze `locker` in `Config.Raid.forces`. Ohne Schrank kann nichts beschlagnahmt werden.
  </Accordion>

  <Accordion title="Beamte oder Gäste in einer Werkstatt sehen die Stationen nicht">
    Das ist so gewollt. Nur Mitglieder des besitzenden Jobs sehen und benutzen die Stationen, Computer und Laptops. Beamte bekommen während einer Razzia eigene Optionen: Beschlagnahmen an den Regalen und am Boss-Laptop, Versiegeln an der Tür.
  </Accordion>

  <Accordion title="Zwei Ausweise öffnen sich gleichzeitig (Qbox)">
    `qbx_idcard` läuft noch. Entferne es: Jaksam Identity antwortet an seiner Stelle, sodass die Starter-Items von qbx_core und qbx_cityhall unverändert weiter funktionieren.
  </Accordion>

  <Accordion title="Die Rechtsklick-Aktionen View, Show und Copy number fehlen (jaksam_inventory)">
    Kopiere `install/jaksam_item_types.lua` nach `jaksam_inventory_data/_data/jksm_identity.lua` und starte `jaksam_inventory` einmal neu. Siehe [Installation](/de/jaksam-identity/installation#items-installieren).
  </Accordion>

  <Accordion title="Dokumente zeigen nichts und melden ein ungültiges Siegel (qb-inventory)">
    qb-inventory übernimmt die Daten eines Items vom Client, deshalb trägt jedes Dokument ein Siegel, das mit einem Schlüssel erstellt wird, den nur der Server kennt. Er liegt in der Tabelle `jksm_identity_settings`.

    Hast du die Datenbank ohne diese Tabelle umgezogen oder zurückgesetzt, hat sich der Schlüssel geändert und die vorhandenen Dokumente haben ihr Siegel verloren. Stelle die Tabelle aus deinem Backup wieder her oder stelle die Dokumente neu aus.
  </Accordion>

  <Accordion title="Der Starter-Ausweis hat kein Foto">
    Das ist so gewollt. Starter-Dokumente werden direkt nach dem Laden des Charakters ausgestellt, ohne Foto. Das Foto wird bei einer Verlängerung in einem [Bürgeramt](/de/jaksam-identity/guides/citizen-offices) aufgenommen.
  </Accordion>

  <Accordion title="In einem Shop gekaufte Dokumente werden als Fälschungen erkannt">
    Ein Dokument aus einem Shop oder einer Admin-Vergabe ist registriert (echt), außer seine jaksam-`rarity` steht in `Config.UnregisteredRarities` (Standard `illegal`). Ändere die Seltenheit des Items oder entferne diese Seltenheit aus der Liste.
  </Accordion>

  <Accordion title="Abgelaufene oder gesperrte Dokumente funktionieren noch">
    Das ist so gewollt: **Fakten, kein Zwang**. Ablauf, Sperren und alte Fotos werden auf der Karte und in der Registerabfrage angezeigt, aber nichts wird automatisch entfernt, blockiert oder verlängert. Was daraus folgt, ist Roleplay.
  </Accordion>

  <Accordion title="Kann die Polizei herausfinden, wer eine Fälschung gemacht hat?">
    Nein. Die Registerabfrage zeigt nur, was eine Behörde wissen würde: kein Eintrag, Status, Ablauf, fehlende Lizenzen, abweichende Daten. Wer sie gemacht hat und ihre Qualität sehen nur Admins mit `/documents truth <serial>`. Wer ein Dokument tatsächlich vorgezeigt hat, wird in `jksm_identity_log` geschrieben, nur für Admins.
  </Accordion>

  <Accordion title="Wie füge ich ein weiteres Dokument oder eine Lizenz hinzu?">
    Füge das Item zu deinem Inventar hinzu, dann einen Eintrag in `Config.Documents` (`config/documents.lua`). Jede Lizenz, die dein Framework kennt, kann ein Dokument werden. Siehe [Eigenes Dokument anlegen](/de/jaksam-identity/guides/documents-and-register#eigenes-dokument-anlegen).
  </Accordion>

  <Accordion title="Wie ändere ich die Sprache oder füge eine neue hinzu?">
    `Config.Locale` wählt die Sprache (`en` und `de` sind dabei), und Admins können sie im Spiel in `/documents config` umschalten. Für eine neue Sprache kopiere `locales/en.lua` nach `locales/<code>.lua`, ändere `Locales['en']` in `Locales['<code>']`, übersetze die Texte und setze den Code in `Config.Locale`. Fehlende Schlüssel fallen auf Englisch zurück.
  </Accordion>

  <Accordion title="Wie nutze ich meine eigenen Benachrichtigungen, Fortschrittsbalken oder Minispiele?">
    - Benachrichtigungen: `bridge/notify.lua`, siehe [Benachrichtigungen](/de/jaksam-identity/client/replace-notifications)
    - Fortschrittsbalken: `Editable.Progress` in `editable/client.lua`, siehe [Fortschrittsbalken](/de/jaksam-identity/client/progress-bar)
    - Minispiel: `Editable.SkillCheck` in `editable/client.lua`, siehe [Skill-Check](/de/jaksam-identity/client/skill-check)
  </Accordion>

  <Accordion title="Ist esx_dmvschool mit diesem Script sicher?">
    Das Event `esx_dmvschool:addLicense` von esx_dmvschool wird auf dem Server nicht geprüft, ein cheatender Client kann sich damit also jede Lizenz geben. Jaksam Identity vertraut den Lizenzen in der Datenbank. Sichere dieses Event in esx_dmvschool ab, oder setze `Config.DmvSchool.enabled = false`, auf einem Live-Server.
  </Accordion>
</AccordionGroup>
