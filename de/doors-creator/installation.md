---
title: "Installation"
description: "Installiere Doors Creator auf deinem FiveM-Server."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

## Voraussetzungen

- Das [Lockpicking-Script](https://github.com/baguscodestudio/lockpick) von [baguscodestudio](https://github.com/baguscodestudio/lockpick)
- Ein `doors_lockpick`-Item, hinzugefügt zu deinem Inventarsystem

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
    Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `doors_creator/sql/` manuell ausführen.
  </Step>
  <Step title="Lockpicking-Script">
    Lade das [Lockpicking-Script](https://github.com/baguscodestudio/lockpick) herunter und starte es _(Credits an [baguscodestudio](https://github.com/baguscodestudio/lockpick))_.
  </Step>
  <Step title="Lockpick-Item hinzufügen">
    Füge das `doors_lockpick`-Item wie bei jedem anderen Script zu deiner Item-Liste hinzu.
  </Step>
  <Step title="Script konfigurieren">
    Konfiguriere das Script über das Ingame-Adminmenü `/doorscreator`.
  </Step>
</Steps>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

Öffne `/doorscreator` im Spiel. Falls sich das Adminmenü öffnet, läuft das Script korrekt.

<Note>
  Sobald die Datenbank erfolgreich eingerichtet wurde, kannst du die SQL-Dateien optional aus `doors_creator/sql/` entfernen, damit das Script nicht bei jedem Start erneut versucht, sie einzurichten.
</Note>
