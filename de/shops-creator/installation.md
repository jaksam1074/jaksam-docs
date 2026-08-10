---
title: "Installation"
description: "Installiere Shops Creator auf deinem FiveM-Server."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

## Voraussetzungen

- Das [Cracking-Safe-Script](https://github.com/VHall1/pd-safe) von [VHall1](https://github.com/VHall1) (falls du das Safe-Cracking-Feature nutzen willst)

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
    Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `shops_creator/sql/` manuell ausführen.
  </Step>
  <Step title="Cracking-Safe-Script">
    Lade das [Cracking-Safe-Script](https://github.com/VHall1/pd-safe) herunter und starte es _(Credits an [VHall1](https://github.com/VHall1))_.
  </Step>
</Steps>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

Öffne `/shopscreator` im Spiel. Falls sich das Menü öffnet, läuft das Script korrekt.

<Note>
  Sobald die Datenbank erfolgreich eingerichtet wurde, kannst du die SQL-Dateien optional aus `shops_creator/sql/` entfernen, damit das Script nicht bei jedem Start erneut versucht, sie einzurichten.
</Note>
