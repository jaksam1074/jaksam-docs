---
title: "Installation"
description: "Installiere Trackers Creator mit ESX oder QBCore auf deinem FiveM-Server, inklusive optionaler Standard-Item-Einrichtung."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

## Voraussetzungen

- **ESX** oder **QBCore**

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
      <Step title="Zum Autostart hinzufügen">
        Füge das Script zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
      <Step title="Datenbank einrichten">
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `trackers_creator/sql/` manuell ausführen.
      </Step>
    </Steps>

    ### Items hinzufügen — Optional

    Um die vorgefertigten Items hinzuzufügen, führe einfach die Datei `trackers_creator/sql/items_limit.sql` **oder** `trackers_creator/sql/items_weight.sql` aus, je nachdem ob dein Server Limit- oder Gewichtsbasis nutzt.

    <Info>
      Die neueste ESX-Version nutzt **Gewicht**.
    </Info>

    <Danger>
      Falls es nicht funktioniert, stelle sicher, dass du die neueste offizielle ESX-Version mit den benötigten Abhängigkeiten verwendest.
    </Danger>
  </Tab>
  <Tab title="QBCore">
    <Steps>
      <Step title="Herunterladen und entpacken">
        Lade das Script herunter und entpacke es in deine Resources.
      </Step>
      <Step title="Zum Autostart hinzufügen">
        Füge das Script zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
      <Step title="Datenbank einrichten">
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `trackers_creator/sql/` manuell ausführen.
      </Step>
    </Steps>

    ### Items hinzufügen — Optional

    Um die neuen Items hinzuzufügen, bearbeite die Datei `qb-core/shared/items.lua` und füge folgenden Code am Ende der Tabelle hinzu:

    ```lua
    ['tracker_sender'] = {['name'] = 'tracker_sender', ['label'] = 'Tracker sender', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = false, ['shouldClose'] = false, ['combinable'] = nil},
    ['tracker_receiver'] = {['name'] = 'tracker_receiver', ['label'] = 'Tracker receiver', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = false, ['shouldClose'] = false, ['combinable'] = nil},
    ['private_tracker'] = {['name'] = 'private_tracker', ['label'] = 'Private tracker', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil},
    ```
  </Tab>
</Tabs>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

<Info>
  [TODO: INFORMATION NEEDED] Für Trackers Creator ist noch keine Ingame-Prüfung für eine erfolgreiche Installation dokumentiert.
</Info>

## Optionaler Schritt

Nachdem die Datenbank korrekt eingerichtet wurde, kannst du die Dateien im Ordner `trackers_creator/sql/` löschen, damit das Script nicht bei jedem Start erneut versucht, die Datenbank einzurichten.
