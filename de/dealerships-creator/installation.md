---
title: "Installation"
description: "Installiere Dealerships Creator auf deinem FiveM-Server, inklusive optionaler automatischer Fahrzeugbild-Erstellung."
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
    Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `dealerships_creator/sql/` manuell ausführen.
  </Step>
</Steps>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

<Info>
  [TODO: INFORMATION NEEDED] Für Dealerships Creator ist noch keine Ingame-Prüfung für eine erfolgreiche Installation dokumentiert.
</Info>

<Note>
  Sobald die Datenbank erfolgreich eingerichtet wurde, kannst du die SQL-Dateien optional aus `dealerships_creator/sql/` entfernen, damit das Script nicht bei jedem Start erneut versucht, sie einzurichten.
</Note>

## Automatische Bilderstellung — Optional

Falls du die automatische Fahrzeugbild-Erstellung nutzen willst, folge diesen Schritten:

<Steps>
  <Step title="screenshot-basic installieren">
    Installiere [screenshot-basic](https://github.com/citizenfx/screenshot-basic) (du hast es wahrscheinlich schon).
  </Step>
  <Step title="yarn installieren">
    Installiere [yarn](https://github.com/citizenfx/cfx-server-data) (du hast es wahrscheinlich schon — `resources/[system]/[builders]`).
  </Step>
  <Step title="webpack installieren">
    Installiere [webpack](https://github.com/citizenfx/cfx-server-data) (du hast es wahrscheinlich schon — `resources/[system]/[builders]`).
  </Step>
  <Step title="Ordnerberechtigungen setzen">
    Stelle sicher, dass der Ordner `dealerships_creator` und der Ordner `dealerships_creator/_vehicles_images` Lese-/Schreibrechte haben (Rechtsklick auf die Ordner → Eigenschaften → Lesen (**R**) und Schreiben (**W**) aktivieren).
  </Step>
</Steps>
