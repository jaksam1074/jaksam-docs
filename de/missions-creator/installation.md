---
title: "Installation"
description: "Installiere Missions Creator mit ESX oder QBCore auf deinem FiveM-Server, inklusive optionaler Minigame-Scripts."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

## Voraussetzungen

- **ESX** oder **QBCore**
- `jaksam_core`, gestartet vor `missions_creator`
- Optionale Minigame-Scripts (siehe letzter Schritt unten), falls du sie nutzen willst

<Danger>
  Verwende **KEIN** FileZilla, um die Dateien hochzuladen, sonst funktioniert das Script **NICHT**.

  Verwende stattdessen [WinSCP](https://winscp.net/eng/download.php).
</Danger>

<Tabs>
  <Tab title="ESX">
    <Steps>
      <Step title="Herunterladen und entpacken">
        Lade das Script herunter und entpacke es in deine Resources.
      </Step>
      <Step title="jaksam_core herunterladen">
        Lade `jaksam_core` herunter und entpacke es in deine Resources.
      </Step>
      <Step title="jaksam_core zum Autostart hinzufügen">
        Füge `jaksam_core` zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
      <Step title="missions_creator zum Autostart hinzufügen">
        Starte `missions_creator` **nach** `jaksam_core`.
      </Step>
      <Step title="Datenbank einrichten">
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `missions_creator/sql/` manuell ausführen.
      </Step>
      <Step title="Optionale Minigame-Scripts">
        - Lade das [Datacrack-Minigame-Script](https://github.com/utkuali/datacrack) herunter und starte es _(Credits an [utkuali](https://github.com/utkuali))_
        - Lade das [Fingerprint-Minigame-Script](https://github.com/utkuali/Finger-Print-Hacking-Game) herunter und starte es _(Credits an [utkuali](https://github.com/utkuali))_
        - Lade das [Memory-Minigame-Script](https://github.com/ultrahacx/ultra-keypackhack) herunter und starte es _(Credits an [ultrahacx](https://github.com/ultrahacx))_
      </Step>
    </Steps>

    <Danger>
      Falls es nicht funktioniert, stelle sicher, dass du die neueste offizielle ESX-Version mit den benötigten Abhängigkeiten verwendest.
    </Danger>
  </Tab>
  <Tab title="QBCore">
    <Steps>
      <Step title="Herunterladen und entpacken">
        Lade das Script herunter und entpacke es in deine Resources.
      </Step>
      <Step title="jaksam_core herunterladen">
        Lade `jaksam_core` herunter und entpacke es in deine Resources.
      </Step>
      <Step title="jaksam_core zum Autostart hinzufügen">
        Füge `jaksam_core` zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
      <Step title="missions_creator zum Autostart hinzufügen">
        Starte `missions_creator` **nach** `jaksam_core`.
      </Step>
      <Step title="Datenbank einrichten">
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `missions_creator/sql/` manuell ausführen.
      </Step>
      <Step title="Optionale Minigame-Scripts">
        - Lade das [Datacrack-Minigame-Script](https://github.com/utkuali/datacrack) herunter und starte es _(Credits an [utkuali](https://github.com/utkuali))_
        - Lade das [Fingerprint-Minigame-Script](https://github.com/utkuali/Finger-Print-Hacking-Game) herunter und starte es _(Credits an [utkuali](https://github.com/utkuali))_
        - Lade das [Memory-Minigame-Script](https://github.com/ultrahacx/ultra-keypackhack) herunter und starte es _(Credits an [ultrahacx](https://github.com/ultrahacx))_
      </Step>
    </Steps>
  </Tab>
</Tabs>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

<Info>
  [TODO: INFORMATION NEEDED] In der Quelldokumentation wird ein Ingame-Adminmenü erwähnt (Missionen verweisen auf ihre ID "die du im Adminmenü siehst"), aber der Befehl zum Öffnen wird nicht genannt. Hier ergänzen, sobald bestätigt.
</Info>

## Optionaler Schritt

Nachdem die Datenbank korrekt eingerichtet wurde, kannst du die Dateien im Ordner `missions_creator/sql/` löschen, damit das Script nicht bei jedem Start erneut versucht, die Datenbank einzurichten.
