---
title: "Installation"
description: "Boosting Creator auf deinem FiveM-Server mit ESX, QBCore oder Qbox installieren, das Laptop-Item hinzufügen und die Admin-Berechtigung vergeben."
icon: "download"
---

Bring **Boosting Creator** auf deinem FiveM-Server zum Laufen.

## Voraussetzungen

| Ressource | Wofür |
| --- | --- |
| `es_extended` **oder** `qb-core` / `qbx_core` | Framework |
| `ox_lib` | Callbacks und optionale Module |
| `oxmysql` (oder `mysql-async`) | Datenbank |
| OneSync | Auftragsautos, Wachen und Verfolger sind vernetzte Entities |
| `vehicles_keys` (optional) | Lockpick und Kurzschließen mit vehicles_keys, temporäre Schlüssel für das gestohlene Auto |
| `datacrack`, `utk_fingerprint`, `ultra-keypackhack` (optional) | Zusätzliche Hack-Minispiele |

<Warning>
  Auftragsautos, Wachen, Garagenautos, der Autotransporter und die verfolgende Gang werden vom Spiel des Diebs erstellt und vom Server geprüft. Mit `sv_entityLockdown strict` kann nichts spawnen und jeder Auftrag wird direkt nach dem Start abgebrochen.
</Warning>

<Danger>
  Verwende **KEIN** FileZilla, um die Dateien hochzuladen, sonst funktioniert das Script **NICHT**.

  Verwende stattdessen [WinSCP](https://winscp.net/eng/download.php).
</Danger>

## Die Ressource installieren

Es gibt eine Version für **ESX** und eine für **QBCore und Qbox**. Nimm die für dein Framework.

<Steps>
  <Step title="Boosting Creator herunterladen">
    Lade die Version für dein Framework herunter und entpacke den Ordner `boosting_creator` in den `resources`-Ordner deines Servers.
  </Step>
  <Step title="server.cfg konfigurieren">
    Starte es **nach** allem, was es braucht, zum Beispiel:

    ```cfg
    ensure oxmysql
    ensure ox_lib
    ensure es_extended
    ensure vehicles_keys
    ensure boosting_creator
    ```
  </Step>
  <Step title="Datenbank">
    Nichts zu tun: Die Tabellen werden beim ersten Start erstellt und neue Spalten kommen mit jedem Update dazu.

    Die Dateien in `boosting_creator/sql/` sind nur für Datenbanken gedacht, in denen das Script keine Tabellen erstellen darf.
  </Step>
  <Step title="Das Laptop-Item hinzufügen">
    Spieler öffnen den Boosting-Laptop mit einem Item, standardmäßig `boosting_laptop`. Siehe [Laptop-Item anlegen](#laptop-item-anlegen) weiter unten.
  </Step>
  <Step title="Die Admin-Berechtigung vergeben">
    Siehe [Admin-Berechtigung](#admin-berechtigung) weiter unten, dann öffne das Panel mit `/boostingcreator`.
  </Step>
</Steps>

## Laptop-Item anlegen

Der Item-Name wird im Panel festgelegt, unter **Einstellungen > Allgemein > Itemname des Laptops**. Eine Änderung braucht einen Neustart des Scripts.

<Tabs>
  <Tab title="jaksam inventory">
    Nichts zu tun: Das Item wird beim Start automatisch erstellt, und erneut, wenn das Inventar neu startet.

    Für das Item-Bild kopiere `boosting_creator/images/boosting_laptop.png` nach `jaksam_inventory_data/_images/`.
  </Tab>
  <Tab title="ox_inventory">
    Füge das zu `ox_inventory/data/items.lua` hinzu:

    ```lua
    ['boosting_laptop'] = {
        label = 'Boosting Laptop',
        weight = 1000,
        stack = false,
        close = true,
        description = 'Contracts for those who know where to look',
    },
    ```

    Das Script hört auf das eigene Use-Event von ox_inventory, kein `server.export` nötig.

    Für das Item-Bild kopiere `boosting_creator/images/boosting_laptop.png` nach `ox_inventory/web/images/`.
  </Tab>
  <Tab title="ESX">
    Führe das auf deiner Datenbank aus:

    ```sql
    INSERT IGNORE INTO `items` (`name`, `label`, `weight`) VALUES ('boosting_laptop', 'Boosting Laptop', 1);
    ```
  </Tab>
  <Tab title="QBCore">
    Füge das zu `qb-core/shared/items.lua` hinzu:

    ```lua
    ['boosting_laptop'] = {['name'] = 'boosting_laptop', ['label'] = 'Boosting Laptop', ['weight'] = 1000, ['type'] = 'item', ['image'] = 'boosting_laptop.png', ['unique'] = true, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Contracts for those who know where to look'},
    ```

    Für das Item-Bild kopiere `boosting_creator/images/boosting_laptop.png` nach `qb-inventory/html/images/`.
  </Tab>
</Tabs>

<Info>
  Existiert das Item nicht, meldet die Server-Konsole das beim Start in Gelb: `The item boosting_laptop doesn't exist, create it in your inventory to use the laptop`.
</Info>

## Admin-Berechtigung

Das Panel und jede Admin-Aktion prüfen ein Ace, standardmäßig `boostingcreator` (änderbar unter **Einstellungen > Allgemein**). Das Ace `jaksam` funktioniert immer zusätzlich.

```cfg
add_ace group.admin boostingcreator allow
```

<Tip>
  Ohne die Berechtigung öffnet `/boostingcreator` ein Fenster mit den genauen `add_ace`-Zeilen für deine eigene License und deinen Steam-Account, fertig zum Kopieren in die `server.cfg`.
</Tip>

## Überprüfung

Öffne im Spiel `/boostingcreator` (oder `/boostcreator`). Öffnet sich das Panel mit den Klassen D bis S schon angelegt, läuft das Script richtig.

Gib dir dann den Laptop, benutze ihn und stell dich in die Warteschlange: Das erste Angebot kommt mit den Standardeinstellungen nach 45 bis 120 Sekunden.

## Aktualisieren

<Warning>
  Sichere vor einem Update `boosting_creator/current_config.json` (alle Einstellungen des Panels) und den Ordner `boosting_creator/integrations/` und setz sie danach in die neue Version ein. Ersetzt du den Ordner ohne sie, kommen die Standardeinstellungen und die Standard-Integrationen zurück.
</Warning>

Klassen, Fahrzeuge, Orte, Fixer und Spielerprofile liegen in der Datenbank und bleiben erhalten. Siehe auch [Scripts aktualisieren](/de/jaksams-scripts/how-to-update-the-scripts).
