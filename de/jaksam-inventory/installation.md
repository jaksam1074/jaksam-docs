---
title: "Installation"
icon: "table-rows-add-below"
description: "Die Installation des Scripts ist sehr einfach."
---

## Voraussetzungen

- **ESX** (1.10.7, 1.11.3+ oder 1.14.0+), **QBCore** oder **QBX**
- `jaksam_core`
- `oxmysql` und `ox_lib` (siehe das Start-Order-Beispiel für dein Framework unten)

<Warning>
  **Verwende KEIN FileZilla**, um die Dateien hochzuladen, sonst funktioniert das Script **NICHT**. Verwende stattdessen [WinSCP](https://winscp.net/eng/download.php).
</Warning>

<Tabs>
  <Tab title="ESX 1.10.7">
    1. Lade das Script herunter und entpacke es in deine Resources.
    2. Lade `jaksam_core` herunter und entpacke es in deine Resources.
    3. Füge folgenden Code **direkt nach** `es_extended` in deine `server.cfg` ein:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Ermöglicht die automatische Selbstinstallation von jaksam's Inventory
    ensure jaksam_inventory
    ```

    4. Setze in `es_extended/config.lua`:

    ```lua
    Config.OxInventory = false
    ```

    5. Setze in `es_extended/config.lua`:

    ```lua
    Config.EnableDefaultInventory = false
    ```

    6. Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `jaksam_inventory/sql/` manuell ausführen.

    ### Start-Order-Beispiel

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## ESX
    ensure es_extended
    ensure jaksam_inventory
    
    # Andere ESX-Scripts
    start [core]
    ```

    <Warning>
      Falls es nicht funktioniert, stelle sicher, dass du die neueste offizielle ESX-Version mit allen benötigten Abhängigkeiten verwendest.
    </Warning>
  </Tab>
  <Tab title="ESX 1.11.3+">
    1. Lade das Script herunter und entpacke es in deine Resources.
    2. Lade `jaksam_core` herunter und entpacke es in deine Resources.
    3. Füge folgenden Code **direkt nach** `es_extended` in deine `server.cfg` ein:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Ermöglicht die automatische Selbstinstallation von jaksam's Inventory
    ensure jaksam_inventory
    ```

    4. Setze in `es_extended/config.lua`:

    ```lua
    Config.CustomInventory = "jaksam_inventory"
    ```

    5. Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `jaksam_inventory/sql/` manuell ausführen.

    ### Start-Order-Beispiel

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## ESX
    ensure es_extended
    ensure jaksam_inventory
    
    # Andere ESX-Scripts
    start [core]
    ```
  </Tab>
  <Tab title="ESX 1.14.0+">
    1. Lade das Script herunter und entpacke es in deine Resources.
    2. Lade `jaksam_core` herunter und entpacke es in deine Resources.
    3. Füge folgenden Code **direkt nach** `es_extended` in deine `server.cfg` ein:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Ermöglicht die automatische Selbstinstallation von jaksam's Inventory
    ensure jaksam_inventory
    ```

    4. Setze in `es_extended/shared/config/main.lua`:

    ```lua
    Config.CustomInventory = "jaksam_inventory"
    ```

    5. Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `jaksam_inventory/sql/` manuell ausführen.

    ### Start-Order-Beispiel

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## ESX
    ensure es_extended
    ensure jaksam_inventory
    
    # Andere ESX-Scripts
    start [core]
    ```
  </Tab>
  <Tab title="QBCore">
    1. Lade das Script herunter und entpacke es in deine Resources.
    2. Lade `jaksam_core` herunter und entpacke es in deine Resources.
    3. Aktiviere `Integrations.backwardsCompatibility` für `qb-inventory` in `jaksam_inventory/integrations/sv_integrations.lua`.
    4. Füge folgenden Code **direkt nach** `qb-core` in deine `server.cfg` ein:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Ermöglicht die automatische Selbstinstallation von jaksam's Inventory
    ensure jaksam_inventory
    ```

    5. Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `jaksam_inventory/sql/` manuell ausführen.

    ### Start-Order-Beispiel

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## QBCore
    ensure qb-core
    ensure jaksam_inventory
    
    # Andere QBCore-Scripts
    ```

    <Warning>
      Falls es nicht funktioniert, stelle sicher, dass du die neueste offizielle QBCore-Version mit allen benötigten Abhängigkeiten verwendest.
    </Warning>
  </Tab>
  <Tab title="QBX">
    1. Lade das Script herunter und entpacke es in deine Resources.
    2. Lade `jaksam_core` herunter und entpacke es in deine Resources.
    3. Aktiviere `Integrations.backwardsCompatibility` für `ox_inventory` in `jaksam_inventory/integrations/sv_integrations.lua`.
    4. Füge folgenden Code **direkt nach** `qbx_core` in deine `server.cfg` ein:

    ```cfg
    add_unsafe_worker_permission jaksam_inventory # Ermöglicht die automatische Selbstinstallation von jaksam's Inventory
    ensure jaksam_inventory
    ```

    5. Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `jaksam_inventory/sql/` manuell ausführen.

    ### Start-Order-Beispiel

    ```cfg
    # OX
    ensure oxmysql
    ensure ox_lib
    
    ## QBX
    ensure qbx_core
    ensure jaksam_inventory
    
    # Andere QBX-Scripts
    ```

    <Warning>
      Falls es nicht funktioniert, stelle sicher, dass du die neueste offizielle QBX-Version mit allen benötigten Abhängigkeiten verwendest.
    </Warning>
  </Tab>
</Tabs>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

Nutze den Befehl `/inventory` im Spiel. Falls sich dein Inventar öffnet, läuft das Script korrekt.

## Alte Items und Inventare importieren

<Tabs>
  <Tab title="ESX">
    1. Geh ins Spiel.
    2. Nutze den Befehl `/inventory` und geh zu **Einstellungen**.
    3. Klicke auf **Import from ESX**.
    4. Fertig!
  </Tab>
  <Tab title="QBCore">
    1. Stelle nur während dieses Vorgangs sicher, dass das **originale `qb-inventory`** läuft. Nach dem Import kannst und solltest du es entfernen.
    2. Nutze den Befehl `/inventory` und geh zu **Einstellungen**.
    3. Klicke auf **Import from QBCore**.
    4. Fertig!
  </Tab>
  <Tab title="OX Inventory">
    1. Stelle nur während dieses Vorgangs sicher, dass `ox_inventory` läuft. Nach dem Import kannst und solltest du es entfernen.
    2. Nutze den Befehl `/inventory` und geh zu **Einstellungen**.
    3. Klicke auf **Import from OX inventory**.
    4. Fertig!
  </Tab>
  <Tab title="qs-inventory">
    1. Stelle nur während dieses Vorgangs sicher, dass `qs-inventory` läuft. Nach dem Import kannst und solltest du es entfernen.
    2. Nutze den Befehl `/inventory` und geh zu **Einstellungen**.
    3. Klicke auf **Import from qs-inventory**.
    4. Fertig!
  </Tab>
  <Tab title="Chezza Inventory">
    1. Stelle nur während dieses Vorgangs sicher, dass das **Chezza-Inventory** läuft. Nach dem Import kannst und solltest du es entfernen.
    2. Nutze den Befehl `/inventory` und geh zu **Einstellungen**.
    3. Klicke auf **Import from Chezza inventory**.
    4. Fertig!
  </Tab>
  <Tab title="TGiann Inventory">
    1. Stelle nur während dieses Vorgangs sicher, dass das **TGiann-Inventory** läuft. Nach dem Import kannst und solltest du es entfernen.
    2. Nutze den Befehl `/inventory` und geh zu **Einstellungen**.
    3. Klicke auf **Import from TGiann inventory**.
    4. Fertig!
  </Tab>
</Tabs>

## Abwärtskompatibilität

Mit diesem Inventar kannst du deine alten Scripts weiterverwenden, auch wenn sie ein anderes Inventarsystem benötigen.

### Standard-Framework-Funktionen

Du kannst die normalen, von deinem Framework bereitgestellten Inventarfunktionen verwenden.

### OX-Inventory-Kompatibilität

Falls deine alten Scripts **OX Inventory** verwenden, kannst du eine einfache Kompatibilität aktivieren.

1. Gehe zu `jaksam_inventory/integrations/sv_integrations.lua`.
2. Aktiviere `ox_inventory` in `Integrations.backwardsCompatibility`.
3. Der Server benötigt eventuell einen Neustart, nachdem er beim ersten Mal mit diesen Einstellungen geladen hat.

### QB-Inventory-Kompatibilität

Falls deine alten Scripts **QB Inventory** verwenden, kannst du eine einfache Kompatibilität aktivieren.

1. Gehe zu `jaksam_inventory/integrations/sv_integrations.lua`.
2. Aktiviere `qb-inventory` in `Integrations.backwardsCompatibility`.
3. Der Server benötigt eventuell einen Neustart, nachdem er beim ersten Mal mit diesen Einstellungen geladen hat.

Das war's! Deine alten Scripts sollten jetzt mit diesem Inventar funktionieren.
