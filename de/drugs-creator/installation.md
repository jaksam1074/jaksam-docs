---
title: "Installation"
description: "Installiere Drugs Creator mit ESX, QBCore oder OX Inventory auf deinem FiveM-Server, inklusive optionaler Standard-Item-Einrichtung."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

## Voraussetzungen

- **ESX**, **QBCore** oder **OX Inventory**

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
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `drugs_creator/sql/` manuell ausführen.
      </Step>
    </Steps>

    ### Items hinzufügen — Optional

    Falls du die vorgefertigten Items/Drogen nutzen willst, folge den Schritten unten.

    Um die vorgefertigten Items/Drogen hinzuzufügen, führe einfach die Datei `drugs_creator/sql/items_limit.sql` **oder** `drugs_creator/sql/items_weight.sql` aus, je nachdem ob dein Server Limit- oder Gewichtsbasis nutzt.

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
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `drugs_creator/sql/` manuell ausführen.
      </Step>
      <Step title="menu_default installieren">
        Lade [menu_default](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) herunter und entpacke es in deine Resources, **ohne es umzubenennen**, und füge es zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
    </Steps>

    ### Items hinzufügen — Optional

    Um die neuen Items hinzuzufügen, bearbeite die Datei `qb-core/shared/items.lua` und füge folgenden Code am Ende der Tabelle hinzu:

    ```lua
    ['ammonium_nitrate'] = {['name'] = 'ammonium_nitrate', ['label'] = 'Ammonium nitrate', ['weight'] = 500, ['type'] = 'item', ['image'] = 'ammonium_nitrate.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['carbon'] = {['name'] = 'carbon', ['label'] = 'Carbon', ['weight'] = 500, ['type'] = 'item', ['image'] = 'carbon.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['codeine'] = {['name'] = 'codeine', ['label'] = 'Codeine', ['weight'] = 500, ['type'] = 'item', ['image'] = 'codeine.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['drink_sprite'] = {['name'] = 'drink_sprite', ['label'] = 'Sprite', ['weight'] = 500, ['type'] = 'item', ['image'] = 'drink_sprite.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['drug_ecstasy'] = {['name'] = 'drug_ecstasy', ['label'] = 'Ecstasy', ['weight'] = 500, ['type'] = 'item', ['image'] = 'drug_ecstasy.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['drug_lean'] = {['name'] = 'drug_lean', ['label'] = 'Lean', ['weight'] = 500, ['type'] = 'item', ['image'] = 'drug_lean.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['drug_lsd'] = {['name'] = 'drug_lsd', ['label'] = 'LSD', ['weight'] = 500, ['type'] = 'item', ['image'] = 'drug_lsd.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['drug_meth'] = {['name'] = 'drug_meth', ['label'] = 'Meth', ['weight'] = 500, ['type'] = 'item', ['image'] = 'drug_meth.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['hydrogen'] = {['name'] = 'hydrogen', ['label'] = 'Hydrogen', ['weight'] = 500, ['type'] = 'item', ['image'] = 'hydrogen.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['ice'] = {['name'] = 'ice', ['label'] = 'Ice', ['weight'] = 500, ['type'] = 'item', ['image'] = 'ice.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['jolly_ranchers'] = {['name'] = 'jolly_ranchers', ['label'] = 'Jolly Ranchers', ['weight'] = 500, ['type'] = 'item', ['image'] = 'jolly_ranchers.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['liquid_sulfur'] = {['name'] = 'liquid_sulfur', ['label'] = 'Liquid Sulfur', ['weight'] = 500, ['type'] = 'item', ['image'] = 'liquid_sulfur.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['muriatic_acid'] = {['name'] = 'muriatic_acid', ['label'] = 'Muriatic Acid', ['weight'] = 500, ['type'] = 'item', ['image'] = 'muriatic_acid.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['nitrogen'] = {['name'] = 'nitrogen', ['label'] = 'Nitrogen', ['weight'] = 500, ['type'] = 'item', ['image'] = 'nitrogen.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['oxygen'] = {['name'] = 'oxygen', ['label'] = 'Oxygen', ['weight'] = 500, ['type'] = 'item', ['image'] = 'oxygen.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['pseudoefedrine'] = {['name'] = 'pseudoefedrine', ['label'] = 'Pseudoefedrine', ['weight'] = 500, ['type'] = 'item', ['image'] = 'pseudoefedrine.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['red_sulfur'] = {['name'] = 'red_sulfur', ['label'] = 'Red Sulfur', ['weight'] = 500, ['type'] = 'item', ['image'] = 'red_sulfur.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['sodium_hydroxide'] = {['name'] = 'sodium_hydroxide', ['label'] = 'Sodium hydroxide', ['weight'] = 500, ['type'] = 'item', ['image'] = 'sodium_hydroxide.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['water'] = {['name'] = 'water', ['label'] = 'Water', ['weight'] = 500, ['type'] = 'item', ['image'] = 'water.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['cannabis'] = {['name'] = 'cannabis', ['label'] = 'Cannabis', ['weight'] = 500, ['type'] = 'item', ['image'] = 'cannabis.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['green_gelato_cannabis'] = {['name'] = 'green_gelato_cannabis', ['label'] = 'Green Gelato Cannabis', ['weight'] = 500, ['type'] = 'item', ['image'] = 'green_gelato_cannabis.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['opium'] = {['name'] = 'opium', ['label'] = 'Opium', ['weight'] = 500, ['type'] = 'item', ['image'] = 'opium.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['cocaine'] = {['name'] = 'cocaine', ['label'] = 'Cocaine', ['weight'] = 500, ['type'] = 'item', ['image'] = 'cocaine.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['meth_raw'] = {['name'] = 'meth_raw', ['label'] = 'Raw Meth', ['weight'] = 500, ['type'] = 'item', ['image'] = 'meth_raw.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['meth_processed'] = {['name'] = 'meth_processed', ['label'] = 'Processed Meth', ['weight'] = 500, ['type'] = 'item', ['image'] = 'meth_processed.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['meth'] = {['name'] = 'meth', ['label'] = 'Meth', ['weight'] = 500, ['type'] = 'item', ['image'] = 'meth.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['cocaine_raw'] = {['name'] = 'cocaine_raw', ['label'] = 'Raw Cocaine', ['weight'] = 500, ['type'] = 'item', ['image'] = 'cocaine_raw.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['cocaine_packaged'] = {['name'] = 'cocaine_packaged', ['label'] = 'Packaged Cocaine', ['weight'] = 500, ['type'] = 'item', ['image'] = 'cocaine_packaged.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
    ['trap_phone'] = {['name'] = 'trap_phone', ['label'] = 'Trap Phone', ['weight'] = 500, ['type'] = 'item', ['image'] = 'trap_phone.png', ['unique'] = true, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil},
    ```

    **Beispiel-Screenshot**

    <Frame>
      ![QBCore Drugs Creator items example](/images/qb_core_drugs_creator_items.jpg)
    </Frame>
  </Tab>
  <Tab title="OX Inventory">
    Hier ist eine Item-Liste für OX Inventory. Du kannst sie auch mit jaksam's Inventory nutzen, über die Einstellung "import from code".

    ```lua
    ['ammonium_nitrate'] = {
        label = 'Ammonium nitrate',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['carbon'] = {
        label = 'Carbon',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['codeine'] = {
        label = 'Codeine',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['drink_sprite'] = {
        label = 'Sprite',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['drug_ecstasy'] = {
        label = 'Ecstasy',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['drug_lean'] = {
        label = 'Lean',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['drug_lsd'] = {
        label = 'LSD',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['drug_meth'] = {
        label = 'Meth',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['hydrogen'] = {
        label = 'Hydrogen',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['ice'] = {
        label = 'Ice',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['jolly_ranchers'] = {
        label = 'Jolly Ranchers',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['liquid_sulfur'] = {
        label = 'Liquid Sulfur',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['muriatic_acid'] = {
        label = 'Muriatic Acid',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['nitrogen'] = {
        label = 'Nitrogen',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['oxygen'] = {
        label = 'Oxygen',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['pseudoefedrine'] = {
        label = 'Pseudoefedrine',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['red_sulfur'] = {
        label = 'Red Sulfur',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['sodium_hydroxide'] = {
        label = 'Sodium hydroxide',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['water'] = {
        label = 'Water',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['cannabis'] = {
        label = 'Cannabis',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['green_gelato_cannabis'] = {
        label = 'Green Gelato Cannabis',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['opium'] = {
        label = 'Opium',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['cocaine'] = {
        label = 'Cocaine',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['meth_raw'] = {
        label = 'Raw Meth',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['meth_processed'] = {
        label = 'Processed Meth',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['meth'] = {
        label = 'Meth',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['cocaine_raw'] = {
        label = 'Raw Cocaine',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['cocaine_packaged'] = {
        label = 'Packaged Cocaine',
        weight = 500,
        stack = true,
        close = false,
    },
    
    ['trap_phone'] = {
        label = 'Trap Phone',
        weight = 500,
        stack = false,
        close = true,
    },
    ```
  </Tab>
</Tabs>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

Öffne `/drugscreator` im Spiel. Falls sich das Menü öffnet, läuft das Script korrekt.

## Optionaler Schritt

Nachdem die Datenbank korrekt eingerichtet wurde, kannst du die Dateien im Ordner `drugs_creator/sql/` löschen, damit das Script nicht bei jedem Start erneut versucht, die Datenbank einzurichten.
