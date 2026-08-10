---
title: "Installation"
description: "Installiere Vehicles Keys mit ESX oder QBCore auf deinem FiveM-Server, inklusive optionaler Standard-Item-Einrichtung."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

## Voraussetzungen

- **ESX** oder **QBCore**
- Das [Lockpicking-Script](https://github.com/baguscodestudio/lockpick) von [baguscodestudio](https://github.com/baguscodestudio/lockpick)
- Bei QBCore das [`menu_default`](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing)-Script

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
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `vehicles_keys/sql/` manuell ausführen.
      </Step>
      <Step title="Lockpicking-Script">
        Lade das [Lockpicking-Script](https://github.com/baguscodestudio/lockpick) herunter und starte es _(Credits an [baguscodestudio](https://github.com/baguscodestudio/lockpick))_.
      </Step>
    </Steps>

    ### Items hinzufügen — Optional

    Um die vorgefertigten Items hinzuzufügen, führe einfach die Datei `vehicles_keys/sql/items_limit.sql` **oder** `vehicles_keys/sql/items_weight.sql` aus, je nachdem ob dein Server Limit- oder Gewichtsbasis nutzt.

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
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `vehicles_keys/sql/` manuell ausführen.
      </Step>
      <Step title="Lockpicking-Script">
        Lade das [Lockpicking-Script](https://github.com/baguscodestudio/lockpick) herunter und starte es _(Credits an [baguscodestudio](https://github.com/baguscodestudio/lockpick))_.
      </Step>
      <Step title="menu_default installieren">
        Lade [menu_default](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) herunter und entpacke es in deine Resources, **ohne es umzubenennen**, und füge es zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
    </Steps>

    ### Items hinzufügen — Optional

    Um die neuen Items hinzuzufügen, bearbeite die Datei `qb-core/shared/items.lua` und füge folgenden Code am Ende der Tabelle hinzu:

    ```lua
    -- Vehicles Keys Items
    ['vehicle_alarm_1'] = {['name'] = 'vehicle_alarm_1', ['label'] = 'Vehicle alarm level 1', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Vehicle alarm level 1'},
    ['vehicle_alarm_2'] = {['name'] = 'vehicle_alarm_2', ['label'] = 'Vehicle alarm level 2', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Vehicle alarm level 2'},
    ['vehicle_alarm_3'] = {['name'] = 'vehicle_alarm_3', ['label'] = 'Vehicle alarm level 3', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Vehicle alarm level 3'},
    ['vehicle_alarm_4'] = {['name'] = 'vehicle_alarm_4', ['label'] = 'Vehicle alarm level 4', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Vehicle alarm level 4'},
    ['vehicle_transfer_contract'] = {['name'] = 'vehicle_transfer_contract', ['label'] = 'Vehicle transfer contract', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Used to sell your vehicle to someone'},
    ```

    <Frame caption="Beispiel-Screenshot">
      ![QBCore Vehicles Keys items example](/images/qb_core_vehicles_keys_items.png)
    </Frame>
  </Tab>
</Tabs>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

<Info>
  [TODO: INFORMATION NEEDED] Für Vehicles Keys ist noch keine Ingame-Prüfung für eine erfolgreiche Installation dokumentiert.
</Info>

## Optionaler Schritt

Nachdem die Datenbank korrekt eingerichtet wurde, kannst du die Dateien im Ordner `vehicles_keys/sql/` löschen, damit das Script nicht bei jedem Start erneut versucht, die Datenbank einzurichten.
