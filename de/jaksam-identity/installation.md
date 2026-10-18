---
title: "Installation"
description: "Jaksam Identity auf deinem FiveM-Server mit ESX, QBCore oder Qbox installieren, die Items zum Inventar hinzufügen und die ersten Ämter und Werkstätten einrichten."
icon: "download"
---

Bring **Jaksam Identity** auf deinem FiveM-Server zum Laufen.

## Voraussetzungen

| Ressource | Wofür |
| --- | --- |
| `es_extended` (mit den esx_license-Tabellen) **oder** `qb-core` / `qbx_core` | Framework |
| `jaksam_inventory` 1.28 oder neuer, **oder** `ox_inventory`, **oder** `qb-inventory` 2.2 (nur QBCore-Version) | Dokumente sind Items mit Daten |
| `ox_lib`, `oxmysql` | Callbacks, Menüs, Datenbank |
| `ox_target` **oder** `qb-target` (nur QBCore-Version) | Targets |
| `bob74_ipl` | Der Innenraum der Fälscherwerkstatt |
| RoadPhone (optional) | Telefonnummern auf Visitenkarten, [Handy-Wallet](/de/jaksam-identity/guides/roadphone-wallet) |
| `esx_dmvschool` (optional, nur ESX) | Der erste Führerschein wird nach der Fahrprüfung ausgestellt |

<Warning>
  Das Script erstellt und aktualisiert seine Datenbanktabellen beim Start selbst. **Sichere deine Datenbank** vor der Installation und vor jedem Update.
</Warning>

## Die Ressource installieren

Es gibt eine Version für **ESX** und eine für **QBCore und Qbox** (sie erkennt selbst, welches der beiden läuft). Nimm die für dein Framework.

<Tabs>
  <Tab title="ESX" icon="server">
    <Steps>
      <Step title="Jaksam Identity herunterladen">
        Lade die ESX-Version herunter und entpacke den Ordner `jksm_identity` in den `resources`-Ordner deines Servers.
      </Step>
      <Step title="server.cfg konfigurieren">
        Starte es **nach** allem, was es braucht, zum Beispiel:

        ```cfg
        ensure oxmysql
        ensure ox_lib
        ensure es_extended
        ensure jaksam_inventory
        ensure ox_target
        ensure bob74_ipl
        ensure jksm_identity
        ```
      </Step>
      <Step title="Datenbank">
        Nichts zu tun: Die Tabellen werden beim Start erstellt und aktualisiert (`jksm_identity_schema` speichert die Version).

        `install/install.sql` ist nur für Datenbanken gedacht, in denen das Script keine Tabellen erstellen darf.
      </Step>
      <Step title="Die Items hinzufügen">
        Füge die Items zu deinem Inventar hinzu, siehe [Items installieren](#items-installieren) weiter unten.
      </Step>
      <Step title="config/main.lua">
        - `Config.Bridge`: Inventar (`'jaksam'` oder `'ox_inventory'`), Benachrichtigungen (`'esx'` oder `'ox_lib'`), Handy (`'roadphone'` oder `'none'`) und Menüs
        - `Config.Locale`: `'en'` oder `'de'`
        - `Config.AdminGroups` / `Config.AdminAce`: wer den Admin-Befehl benutzen darf
        - `Config.Debug = false` auf einem Live-Server
      </Step>
    </Steps>

    <Warning>
      **esx_dmvschool:** Sein Event `esx_dmvschool:addLicense` wird auf dem Server nicht geprüft, ein cheatender Client kann sich damit also jede Lizenz geben. Jaksam Identity vertraut den Lizenzen in der Datenbank und stellt mit `Config.DmvSchool` nach diesem Event den Führerschein aus. Sichere das Event in esx_dmvschool ab, oder setze `Config.DmvSchool.enabled = false`, auf einem Live-Server.
    </Warning>
  </Tab>
  <Tab title="QBCore / Qbox" icon="server">
    <Steps>
      <Step title="Jaksam Identity herunterladen">
        Lade die QBCore-Version herunter und entpacke den Ordner `jksm_identity` in den `resources`-Ordner deines Servers.
      </Step>
      <Step title="qbx_idcard entfernen (Qbox)">
        Jaksam Identity übernimmt seinen Platz: Es antwortet auf den Namen `qbx_idcard`, auf seine Exports `GetMetaLicense` und `CreateMetaLicense` und auf sein Show-Event, sodass die Starter-Items von qbx_core und qbx_cityhall unverändert weiter funktionieren.

        <Warning>
          Läuft `qbx_idcard` noch, öffnen sich zwei Karten.
        </Warning>
      </Step>
      <Step title="server.cfg konfigurieren">
        Starte es **nach** allem, was es braucht, zum Beispiel:

        ```cfg
        ensure oxmysql
        ensure ox_lib
        ensure qb-core
        ensure qb-inventory
        ensure qb-target
        ensure bob74_ipl
        ensure jksm_identity
        ```
      </Step>
      <Step title="Datenbank">
        Nichts zu tun: Die Tabellen werden beim Start erstellt und aktualisiert (`jksm_identity_schema` speichert die Version).

        `install/install.sql` ist nur für Datenbanken gedacht, in denen das Script keine Tabellen erstellen darf.
      </Step>
      <Step title="Die Items hinzufügen">
        Füge die Items zu deinem Inventar hinzu, siehe [Items installieren](#items-installieren) weiter unten.
      </Step>
      <Step title="config/main.lua">
        - `Config.Bridge.framework = 'auto'` erkennt, ob qb-core oder qbx_core läuft
        - `Config.Bridge.target = 'auto'` nutzt ox_target, wenn es installiert ist, sonst qb-target
        - `Config.Bridge.inventory`: `'jaksam'`, `'ox_inventory'` oder `'qb-inventory'`
        - `Config.Locale`: `'en'` oder `'de'`
        - `Config.AdminGroups` / `Config.AdminAce`: wer den Admin-Befehl benutzen darf
        - `Config.Debug = false` auf einem Live-Server
      </Step>
    </Steps>

    <Info>
      - **Items:** Personalausweis, Führerschein und Waffenschein sind die eigenen QBCore-Items `id_card`, `driver_license` und `weaponlicense`. Dienstausweise, Visitenkarten und das Werkstattmaterial sind Items dieses Scripts.
      - **Starter-Items und Rathaus:** Was qb-core, qbx_core und qb-cityhall / qbx_cityhall ausgeben, wird zu einem registrierten Dokument des Charakters. qbx_cityhall stellt es mit einem dort aufgenommenen Foto aus.
      - **Alte Kartenfelder:** Jede Karte trägt zusätzlich `citizenid`, `birthdate`, `nationality` und `cardtype` für Scripts, die sie lesen.
      - **Lizenzen** kommen aus den Charakter-Metadaten `licences` (`driver` ist das `drive` des Scripts).
      - **Schwarzgeld:** Auf QBCore das Item `markedbills` (Wert in `metadata.worth`), auf Qbox das stapelbare Item `black_money`.
      - Die esx_dmvschool-Unterstützung gibt es nur in der ESX-Version.
    </Info>
  </Tab>
</Tabs>

## Items installieren

<Tabs>
  <Tab title="jaksam_inventory" icon="boxes-stacked">
    <Steps>
      <Step title="Die Item-Einträge hinzufügen">
        Füge die Einträge aus `install/jaksam_items.lua` in `jaksam_inventory_data/items.lua` ein, innerhalb der Tabelle nach `return { }`.
      </Step>
      <Step title="Die Item-Typen hinzufügen">
        Kopiere `install/jaksam_item_types.lua` unverändert nach `jaksam_inventory_data/_data/jksm_identity.lua`. Es fügt die Rechtsklick-Aktionen **View**, **Show** und **Copy number** hinzu. Nichts einzufügen: Dateien in diesem Ordner überstehen Inventar-Updates.
      </Step>
      <Step title="Die Bilder kopieren">
        Kopiere `install/images/*.webp` nach `jaksam_inventory_data/_images/`.
      </Step>
      <Step title="Das Inventar neu starten">
        Starte `jaksam_inventory` einmal neu.
      </Step>
    </Steps>

    Siehe [Items aus Shops oder Admin-Vergaben](#items-aus-shops-oder-admin-vergaben) für den Metadaten-Block, den jedes Dokument-Item behalten muss.
  </Tab>
  <Tab title="ox_inventory" icon="box">
    Setze `Config.Bridge.inventory = 'ox_inventory'` und `Config.InventoryKeys = { 'TAB' }` (die Taste, die das Inventar neben einer offenen Karte öffnet).

    <Steps>
      <Step title="Die Items hinzufügen">
        Füge `install/ox_items.lua` zu `ox_inventory/data/items.lua` hinzu.
      </Step>
      <Step title="Die Bilder kopieren">
        Kopiere `install/images/*.webp` nach `ox_inventory/web/images/`.
      </Step>
    </Steps>

    - Die Dokumente bekommen einen Use-Export (zeigen oder ansehen, `Config.UseAction`) und die Rechtsklick-Buttons **View** und **Show**. Die Nummer kopierst du mit dem ox_inventory-eigenen "Copy serial number".
    - **Dokumente aus Shops und Admin-Vergaben** bekommen ihre Daten vom Script über den `createItem`-Hook von ox, ohne Metadaten in den Item-Definitionen.
    - **ID-Stapel** sind ox-Container, vom Script eingerichtet. Eine Brieftasche zählt für die Handy-Wallet nur, wenn sie ein ox-Container ist (`setContainerProperties`) und in `Config.WalletContainers` steht. ox erlaubt keinen Container in einem anderen Container.
    - **Dokumente auf dem Boden** kann ansehen, wer diesen Drop geöffnet hat.
  </Tab>
  <Tab title="qb-inventory" icon="box-open">
    Nur QBCore-Version, gebaut für **qb-inventory 2.2**. Setze `Config.Bridge.inventory = 'qb-inventory'` und `Config.InventoryKeys = { 'TAB' }`.

    <Steps>
      <Step title="Die Items hinzufügen">
        Füge `install/qb_items.lua` zu `qb-core/shared/items.lua` hinzu und ersetze dabei die drei Karten-Items, die QBCore schon hat.
      </Step>
      <Step title="Die Bilder kopieren">
        Kopiere `install/images/*.webp` nach `qb-inventory/html/images/`.
      </Step>
    </Steps>

    In qb-inventory muss nichts geändert werden, und sein eigener Chat-Ausweis erscheint nicht mehr.

    - **Ein Dokument benutzen** zeigt oder öffnet es (`Config.UseAction`). qb-inventory hat keine Rechtsklick-Buttons, setze also `Config.UseAction = 'menu'`, um jedes Mal zwischen Ansehen und Zeigen zu wählen. Eine Visitenkarte fragt immer (ansehen, zeigen, übergeben). Die Nummer wird aus der offenen Karte kopiert.
    - **Dokumente aus Starter-Items, dem Rathaus, einem Shop oder `/giveitem`** bekommen ihre Daten vom Script (Hook `ItemAdded` von qb-inventory).
    - **Keine ID-Stapel:** qb-inventory hat keine Container. Die Dokumente eines Auftrags kommen einzeln im Ergebnislager an, und die Handy-Wallet liest nur das Hauptinventar.
    - **Ein Lager ist für einen Spieler gleichzeitig offen** (Regel von qb-inventory). Was die Arbeiter hineinlegen, während es offen ist, siehst du nach erneutem Öffnen.

    <Warning>
      **Versiegelte Dokumente:** qb-inventory übernimmt die Daten eines Items vom Client, wenn ein Spieler es gibt oder fallen lässt. Jedes Dokument trägt deshalb ein Siegel, das mit einem Schlüssel erstellt wird, den nur der Server kennt (Tabelle `jksm_identity_settings`, beim ersten Start erstellt). Ein Dokument mit erfundenen oder geänderten Daten hat kein gültiges Siegel: Es zeigt nichts und sagt das auch. **Behalte diese Tabelle, wenn du die Datenbank umziehst**, sonst verlieren die Dokumente in den Inventaren ihr Siegel.
    </Warning>
  </Tab>
</Tabs>

### Items aus Shops oder Admin-Vergaben

Wenn das Script ein Dokument ausstellt, übergibt es die Metadaten selbst. Entsteht ein Dokument-Item auf anderem Weg (ein jaksam-Shop, eine Admin-Vergabe), füllen die Metadaten-Templates es. Die Einträge in `install/jaksam_items.lua` haben diesen Block schon, behalte ihn bei jedem Dokument-Item:

```lua
dynamicMetadata = {
    serial    = { metadataTemplateId = 'doc_serial',    onlyFirstAdd = true },
    firstname = { metadataTemplateId = 'doc_firstname', onlyFirstAdd = true },
    lastname  = { metadataTemplateId = 'doc_lastname',  onlyFirstAdd = true },
    dob       = { metadataTemplateId = 'doc_dob',       onlyFirstAdd = true },
    sex       = { metadataTemplateId = 'doc_sex',       onlyFirstAdd = true },
    issued    = { metadataTemplateId = 'doc_issued',    onlyFirstAdd = true },
    expires   = { metadataTemplateId = 'doc_expires',   onlyFirstAdd = true },
    classes   = { metadataTemplateId = 'doc_classes',   onlyFirstAdd = true }, -- only with licence classes
},
```

Die Templates werden beim Start registriert und erneut, wann immer jaksam_inventory neu startet. Ein durch ein Template erstelltes Dokument ist **registriert** (echt), außer seine jaksam-`rarity` steht in `Config.UnregisteredRarities` (Standard `illegal`).

## Konfigurieren

<Steps>
  <Step title="config/documents.lua">
    Die Dokumenttypen, ihre Items, Gültigkeit und Themes. Jede Lizenz, die dein Framework kennt, kann ein Dokument werden: Füge das Item und einen Eintrag hier hinzu. Siehe [Dokumente und Register](/de/jaksam-identity/guides/documents-and-register).
  </Step>
  <Step title="config/office.lua">
    Die Starter-Dokumente (`Config.Starter`, standardmäßig der Personalausweis) und die Bürgerämter (`Config.Offices`): Orte, NPC-Modelle, welche Dokumente jedes Amt bearbeitet, Gebühren, bar oder Bank. Siehe [Bürgerämter](/de/jaksam-identity/guides/citizen-offices).
  </Step>
  <Step title="config/forgery.lua">
    Trage die Fälscherwerkstätten in `Config.Forgery.workshops` ein (Eingang draußen, Preis, die Jobs, die sie besitzen dürfen), oder füge sie im Spiel mit `/documents config` hinzu. **Ab Werk ist keine Werkstatt eingerichtet**: Die Fälscherseite bleibt unsichtbar, bis du eine hinzufügst. Siehe [Fälscherwerkstätten](/de/jaksam-identity/guides/forgery-workshops).
  </Step>
  <Step title="config/raid.lua">
    Die Einheiten, die Werkstätten stürmen (deine Polizei-Jobs, ab welchem Rang), und wo der Asservatenschrank jeder Einheit steht. Ohne Schrank kann nichts beschlagnahmt werden. `Config.Raid.enabled = false` schaltet Razzien ab. Siehe [Razzien](/de/jaksam-identity/guides/raids).
  </Step>
</Steps>

<Tip>
  Die meisten dieser Einstellungen, Orte eingeschlossen, kannst du im Spiel mit `/documents config` ändern, ohne Dateien zu bearbeiten oder neu zu starten. Siehe [Einstellungen im Spiel](/de/jaksam-identity/guides/settings-in-game).
</Tip>

## Überprüfung

Starte den Server und lies die Konsole. Eine fehlende Ressource oder eine Bridge ohne Datei wird rot genannt. **Keine rote Zeile bedeutet, dass die Startprüfungen bestanden sind** (mit `Config.Debug = true` gibt es zusätzlich `start checks passed` aus).

Öffne im Spiel als Admin `/documents`: Ohne Unterbefehl listet es alle verfügbaren auf.
