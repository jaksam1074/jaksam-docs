---
title: "Installation"
description: "Installiere Easy Allowlist & Queue auf deinem FiveM-Server."
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
    Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `easy_allowlist/sql/` manuell ausführen.
  </Step>
  <Step title="Dich selbst whitelisten">
    Um dich selbst zur Allowlist hinzuzufügen, verwende den Befehl `add_allowlist DEINE_REQUEST_ID` in der Serverkonsole, nachdem du die Anfrage gesendet hast.
  </Step>
  <Step title="Ingame-Einstellungen konfigurieren">
    Richte die Ingame-Einstellungen ebenfalls gemäß dieser Anleitung ein.
  </Step>
</Steps>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

Führe `add_allowlist DEINE_REQUEST_ID` in der Serverkonsole aus (gemäß dem Schritt "Dich selbst whitelisten" oben). Falls der Befehl erkannt wird und ohne "Unknown command"-Fehler ausgeführt wird, läuft das Script korrekt.

<Note>
  Sobald die Datenbank erfolgreich eingerichtet wurde, kannst du die SQL-Dateien optional aus `easy_allowlist/sql/` entfernen, damit das Script nicht bei jedem Start erneut versucht, sie einzurichten.
</Note>
