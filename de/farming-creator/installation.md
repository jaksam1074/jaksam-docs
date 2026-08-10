---
title: "Installation"
description: "Installiere Farming Creator mit ESX oder QBCore auf deinem FiveM-Server."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

## Voraussetzungen

- **ESX** oder **QBCore**
- Bei QBCore das [`menu_default`](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing)-Script

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
    Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `farming_creator/sql/` manuell ausführen.
  </Step>
  <Step title="menu_default installieren (nur QBCore)">
    Lade [menu_default](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) herunter und entpacke es in deine Resources, **ohne es umzubenennen**, und füge es zu deinem Autostart hinzu (Beispiel: `server.cfg`).
  </Step>
</Steps>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

<Info>
  [TODO: INFORMATION NEEDED] Für Farming Creator ist noch keine Ingame-Prüfung für eine erfolgreiche Installation dokumentiert.
</Info>

<Note>
  Sobald die Datenbank erfolgreich eingerichtet wurde, kannst du die SQL-Dateien optional aus `farming_creator/sql/` entfernen, damit das Script nicht bei jedem Start erneut versucht, sie einzurichten.
</Note>
