---
title: "Installation"
description: "Installiere Blips Creator auf deinem FiveM-Server."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

<Danger>
  Verwende **KEIN** FileZilla, um die Dateien hochzuladen, sonst funktioniert das Script **NICHT**.

  Verwende stattdessen [WinSCP](https://winscp.net/eng/download.php).
</Danger>

<Steps>
  <Step title="Herunterladen und entpacken">
    Lade das Script herunter und entpacke es in deine Resources.
  </Step>
  <Step title="Zum Autostart hinzufügen">
    Füge das Script zu deinem Autostart hinzu (Beispiel: `server.cfg`).
  </Step>
  <Step title="Datenbank einrichten">
    Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `blips_creator/sql/` manuell ausführen.
  </Step>
  <Step title="Optionen konfigurieren">
    Konfiguriere die Optionen in den Config-Dateien (lies die Kommentare, sie erklären alles).
  </Step>
  <Step title="Menü öffnen">
    Um das Menü zu öffnen, drücke `LEERTASTE`, während du dich auf der Ingame-Übersichtskarte befindest.
  </Step>
</Steps>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

Drücke `LEERTASTE`, während du dich auf der Ingame-Übersichtskarte befindest. Falls sich das Blips-Menü öffnet, läuft das Script korrekt.

<Note>
  Sobald die Datenbank erfolgreich eingerichtet wurde, kannst du die SQL-Dateien optional aus `blips_creator/sql/` entfernen, damit das Script nicht bei jedem Start erneut versucht, sie einzurichten.
</Note>
