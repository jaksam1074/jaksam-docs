---
title: "Installation"
description: "Installiere Jobs Creator mit ESX oder QBCore auf deinem FiveM-Server. Folge der frameworkspezifischen Einrichtung und konfiguriere die benötigte Datenbank und Items."
icon: "download"
---

Bring **Jobs Creator** in wenigen Schritten auf deinem FiveM-Server zum Laufen.

## Voraussetzungen

- **ESX** oder **QBCore**
- Bei QBCore das [`menu_default`](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing)-Script (siehe Schritt 4 unten)

Wähle unten dein Framework, um die passende Installationsanleitung zu sehen.

<Tabs>
  <Tab title="ESX" icon="server">
    <Steps>
      <Step title="Jobs Creator herunterladen">
        Lade **Jobs Creator** herunter und entpacke es in den `resources`-Ordner deines Servers.
      </Step>
      <Step title="server.cfg konfigurieren">
        Füge Folgendes zu deiner `server.cfg` hinzu:

        ```cfg
        add_unsafe_worker_permission jobs_creator # Ermöglicht die automatische Selbstinstallation von jobs_creator
        ensure jobs_creator
        ```
      </Step>
      <Step title="Datenbank einrichten">
        Jobs Creator richtet die Datenbank **automatisch** ein, sobald die Resource startet.

        Falls die automatische Einrichtung fehlschlägt, kannst du die SQL-Dateien manuell ausführen, sie liegen in:

        ```text
        jobs_creator/sql/
        ```
      </Step>
      <Step title="Enthaltene Items hinzufügen">
        <Note>
          Das Hinzufügen der enthaltenen Items ist **optional**. Wähle die SQL-Datei passend zu deinem ESX-Inventarsystem.
        </Note>

        **Gewichtsbasiertes Inventar**

        Führe aus:

        ```text
        jobs_creator/sql/items_weight.sql
        ```

        **Limitbasiertes Inventar**

        Führe aus:

        ```text
        jobs_creator/sql/items_limit.sql
        ```
      </Step>
    </Steps>
  </Tab>
  <Tab title="QBCore" icon="server">
    <Steps>
      <Step title="Jobs Creator herunterladen">
        Lade **Jobs Creator** herunter und entpacke es in den `resources`-Ordner deines Servers.
      </Step>
      <Step title="server.cfg konfigurieren">
        Füge Folgendes zu deiner `server.cfg` hinzu:

        ```cfg
        add_unsafe_worker_permission jobs_creator # Ermöglicht die automatische Selbstinstallation von jobs_creator
        ensure jobs_creator
        ```
      </Step>
      <Step title="Datenbank einrichten">
        Jobs Creator richtet die Datenbank **automatisch** ein, sobald die Resource startet.

        Falls die automatische Einrichtung fehlschlägt, kannst du die SQL-Dateien manuell ausführen, sie liegen in:

        ```text
        jobs_creator/sql/
        ```
      </Step>
      <Step title="menu_default installieren">
        Lade [`menu_default`](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) herunter und entpacke es in den `resources`-Ordner deines Servers.

        Füge dann `menu_default` zu deiner `server.cfg` hinzu:

        ```cfg
        ensure menu_default
        ```
      </Step>
      <Step title="Enthaltene Items hinzufügen">
        <Note>
          Das Hinzufügen der enthaltenen Items ist **optional**.
        </Note>

        Öffne:

        ```text
        qb-core/shared/items.lua
        ```

        Füge folgende Items am Ende der Items-Tabelle hinzu:

        ```lua
        ['fixkit'] = {
            ['name'] = 'fixkit',
            ['label'] = 'Fixkit',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['medikit'] = {
            ['name'] = 'medikit',
            ['label'] = 'Medikit',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['sponge'] = {
            ['name'] = 'sponge',
            ['label'] = 'Sponge',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['handcuffs'] = {
            ['name'] = 'handcuffs',
            ['label'] = 'Handcuffs',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['lockpick'] = {
            ['name'] = 'lockpick',
            ['label'] = 'Lockpick',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        
        ['bandage'] = {
            ['name'] = 'bandage',
            ['label'] = 'Bandage',
            ['weight'] = 500,
            ['type'] = 'item',
            ['image'] = 'your_image.png',
            ['unique'] = false,
            ['useable'] = false,
            ['shouldClose'] = false,
            ['combinable'] = nil
        },
        ```
      </Step>
    </Steps>
  </Tab>
</Tabs>

## Verifizierung

Öffne `/jobscreator` im Spiel. Falls sich das Menü öffnet, läuft das Script korrekt.

## SQL-Dateien aufräumen

<Note>
  Sobald die Datenbank erfolgreich eingerichtet wurde, kannst du die SQL-Dateien optional aus `jobs_creator/sql/` entfernen.
</Note>

Die SQL-Dateien werden nur für die manuelle Datenbankeinrichtung oder beim Hinzufügen der enthaltenen ESX-Items benötigt.
