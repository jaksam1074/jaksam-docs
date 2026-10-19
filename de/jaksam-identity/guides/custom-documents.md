---
title: "Eigenes Dokument erstellen"
description: "Füge Jaksam Identity deinen eigenen Ausweis, deine eigene Lizenz oder deinen eigenen Dienstausweis hinzu, Schritt für Schritt: das Item, der Dokumenttyp, sein Aussehen, wo es ausgestellt wird und wie du es testest."
icon: "pen-ruler"
---

Ein Dokument besteht aus zwei Dingen: **einem Item in deinem Inventar** und **einem Eintrag in `Config.Documents`** (`config/documents.lua`). Diese Seite baut zwei Beispiele von Grund auf:

- einen **Jagdschein**, ein `license`-Dokument, das in einem Bürgeramt ausgestellt wird
- einen **Feuerwehr-Dienstausweis**, ein `badge`-Dokument für den Job `fire`

Dieselben Schritte gelten für jede andere Karte. Was die drei Arten im Register bedeuten, steht in [Dokumente und Register](/de/jaksam-identity/guides/documents-and-register).

## Die Art wählen

| Art | Wofür | Das Register sagt gültig, solange |
| --- | --- | --- |
| `identity` | Personalausweise, Reisepässe, Aufenthaltstitel | der Status des Eintrags gültig ist |
| `license` | Alles, was auf einer Lizenz deines Frameworks beruht | der Status gültig ist **und** der Charakter die Lizenz noch hat |
| `badge` | Dienstausweise eines Jobs | der Status gültig ist **und** der Inhaber den Job noch hat |

## Schritt für Schritt

<Steps>
  <Step title="Prüfen, dass die Lizenz existiert (nur license)">
    <Tabs>
      <Tab title="ESX">
        Der Lizenztyp muss eine Zeile der esx_license-Tabelle `licenses` sein. Wenn kein anderes Script ihn anlegt, leg ihn selbst an:

        ```sql
        INSERT INTO licenses (type, label) VALUES ('hunting', 'Hunting licence');
        ```

        Fehlt er, schreibt die Konsole beim Start `hunting: licence type "hunting" is not in the licenses table`.
      </Tab>
      <Tab title="QBCore / Qbox">
        Nichts anzulegen: Die Lizenz ist der Schlüssel `hunting` in den Charakter-Metadaten `licences`. Jeder Lizenztyp, den ein Dokument verwendet, ist dem Script bekannt.
      </Tab>
    </Tabs>
  </Step>

  <Step title="Das Item hinzufügen">
    Der Item-Name ist frei wählbar, er muss nur mit `item` im nächsten Schritt übereinstimmen. Gib ihm ein Bild mit dem Namen des Items (zum Beispiel `hunting_license.webp`) im Bildordner deines Inventars.

    <Tabs>
      <Tab title="jaksam_inventory">
        Füge es zu `jaksam_inventory_data/items.lua` hinzu. `type = 'idcards'` gibt ihm die Rechtsklick-Aktionen **View**, **Show** und **Copy number**, `onUse` übergibt es dem Script und `dynamicMetadata` füllt ein Dokument, das aus einem Shop oder einem Admin-Give kommt:

        ```lua
        ['hunting_license'] = {
            label = 'Hunting licence',
            weight = 0.01,
            stackable = false,
            close = true,
            type = 'idcards',
            onUse = function(playerId, inventoryId, slotId)
                TriggerEvent('jksm_identity:use', playerId, inventoryId, slotId)
            end,
            dynamicMetadata = {
                serial = { metadataTemplateId = 'doc_serial', onlyFirstAdd = true },
                firstname = { metadataTemplateId = 'doc_firstname', onlyFirstAdd = true },
                lastname = { metadataTemplateId = 'doc_lastname', onlyFirstAdd = true },
                dob = { metadataTemplateId = 'doc_dob', onlyFirstAdd = true },
                sex = { metadataTemplateId = 'doc_sex', onlyFirstAdd = true },
                issued = { metadataTemplateId = 'doc_issued', onlyFirstAdd = true },
                expires = { metadataTemplateId = 'doc_expires', onlyFirstAdd = true },
            },
            displayFields = {
                { field = 'lastname', label = 'Last name: ${value}' },
                { field = 'firstname', label = 'First name: ${value}' },
                { field = 'serial', label = 'No.: ${value}' },
                { field = 'expires', label = 'Valid until: ${value}' },
            },
        },
        ```

        - Eine Lizenz mit **Klassen** braucht zusätzlich `classes = { metadataTemplateId = 'doc_classes', onlyFirstAdd = true }`
        - Ein **Dienstausweis** braucht zusätzlich `rank = { metadataTemplateId = 'doc_rank', onlyFirstAdd = true }`

        Starte `jaksam_inventory` einmal neu.
      </Tab>
      <Tab title="ox_inventory">
        Füge es zu `ox_inventory/data/items.lua` hinzu. Die Daten von Dokumenten aus Shops und Admin-Gives kommen vom Script, hier sind keine Metadaten nötig:

        ```lua
        ['hunting_license'] = {
            label = 'Hunting licence', weight = 10, stack = false, close = true, consume = 0,
            client = { image = 'hunting_license.webp' },
            server = { export = 'jksm_identity.useDocument' },
            buttons = {
                { label = 'View', action = function(slot) exports.jksm_identity:viewSlot(slot) end },
                { label = 'Show', action = function(slot) exports.jksm_identity:showSlot(slot) end },
            },
        },
        ```
      </Tab>
      <Tab title="qb-inventory">
        Füge es zu `qb-core/shared/items.lua` hinzu. Das Benutzen übernimmt das Script, sobald das Item in `Config.Documents` steht:

        ```lua
        hunting_license = { name = 'hunting_license', label = 'Hunting licence', weight = 10, type = 'item', image = 'hunting_license.webp', unique = true, useable = true, shouldClose = true, description = 'Permit to hunt' },
        ```
      </Tab>
    </Tabs>
  </Step>

  <Step title="Den Dokumenttyp hinzufügen">
    Ein Eintrag in `Config.Documents`. Der Schlüssel (`hunting`, `badge_fd`) ist der **Dokumenttyp**: Er wird im Register gespeichert und von den Ämtern, den Befehlen und den Exports verwendet. Benenne ihn nicht um, sobald es Dokumente dieses Typs gibt.

    ```lua
    hunting = {
        item = 'hunting_license',
        kind = 'license',
        license = 'hunting',
        label = 'Hunting licence',
        validityDays = 120,
        theme = { header = 'STATE OF SAN ANDREAS', title = 'HUNTING LICENSE', primary = '#2f4a2a', secondary = '#f1efe4', accent = '#c07a2c' },
    },

    badge_fd = {
        item = 'fd_identity',
        kind = 'badge',
        job = 'fire',
        label = 'LSFD badge',
        layout = 'badge',
        theme = { header = 'CITY OF LOS SANTOS', title = 'FIRE DEPARTMENT', word = 'FIRE', emblem = 'shield', primary = '#8a1c12', secondary = '#f5ede6', accent = '#e0a526', authority = 'FIRE CHIEF', authorityName = '' },
    },
    ```

    | Feld | Beschreibung |
    | --- | --- |
    | `item` | Das Item aus dem vorigen Schritt |
    | `kind` | `identity`, `license` oder `badge` |
    | `license` | (`license`) der Lizenztyp |
    | `licenses` | (`license`, statt `license`) mehrere Lizenztypen, als Klassen gedruckt, zum Beispiel `{ boat_small = 'A', boat_large = 'B' }` |
    | `job` | (`badge`) der Job, zu dem der Dienstausweis gehört |
    | `label` | Name in Menüs und Ämtern. Ein einfacher Text oder ein Locale-Schlüssel mit `L('...')` |
    | `validityDays` | Tage bis zum Ablauf, `nil` für nie |
    | `layout` | `id` (Querformat, Standard) oder `badge` (Dienstausweis im Hochformat) |
    | `theme` | Das Aussehen, siehe [Das Aussehen der Karte](#das-aussehen-der-karte) |
  </Step>

  <Step title="Festlegen, wer es ausstellt">
    <Tabs>
      <Tab title="identity / license">
        Trage den Typ in die `documents` eines Amts ein und gib ihm seine Gebühren in `Config.Offices` (`config/office.lua`), oder auf der Ämter-Seite von `/documents config`:

        ```lua
        fees = {
            hunting = { first = 300, renew = 120, replace = 350 },
        },
        locations = {
            { label = 'Ranger station', coords = vec4(0.0, 0.0, 0.0, 0.0), model = 's_m_y_ranger_01', documents = { 'hunting' } },
        },
        ```

        Ohne ein Amt, das es führt, existiert das Dokument, aber **kein Schalter gibt es aus**. Eine Lizenz wird nur an Charaktere ausgestellt, die sie haben: Das Amt erteilt sie nicht.

        Ein `identity`-Dokument kann auch jeder neue Charakter bekommen: Trage den Typ in `Config.Starter.documents` ein. Siehe [Bürgerämter](/de/jaksam-identity/guides/citizen-offices).
      </Tab>
      <Tab title="badge">
        Dienstausweise werden nie in einem Amt ausgestellt. Stell sie mit dem Admin-Befehl aus, oder aus deinem eigenen Boss-Menü mit dem Export `Issue`:

        ```lua
        local serial, reason = exports["jksm_identity"]:Issue(employeeId, "badge_fd", { issuerSrc = bossId })
        ```

        Der Mitarbeiter muss den Job des Dienstausweises haben, sonst ist `reason` gleich `wrong_job`. Um einzuschränken, wer ihn ausstellen darf, nutze den [CanIssue-Hook](/de/jaksam-identity/server/hooks/can-issue). Siehe [Ausstellen](/de/jaksam-identity/server/register/issue).
      </Tab>
    </Tabs>
  </Step>

  <Step title="Neu starten und testen">
    Starte `jksm_identity` neu, dann im Spiel:

    ```bash
    /documents issue <your id> hunting grant    # grant gives the licence first
    /documents issue <your id> badge_fd force   # force skips the job check
    ```

    Benutze das Item, um es anzusehen, und prüfe es mit `/documents check <serial>`.
  </Step>
</Steps>

## Das Aussehen der Karte

Jedes Feld von `theme` ist optional.

| Feld | Wo es erscheint |
| --- | --- |
| `header` | Kleine Zeile oben. Standard `STATE OF SAN ANDREAS` |
| `title` | Großer Titel auf der Vorderseite (bei Dienstausweisen auch auf der Rückseite). Standard das `label` in Großbuchstaben |
| `primary` | Das farbige Band oben, das Wortband der Dienstausweise und das Innere des Emblems. Auch die Farbe des Dokuments in der [Handy-Wallet](/de/jaksam-identity/guides/roadphone-wallet) |
| `secondary` | Der Hintergrund der Karte |
| `accent` | Die Linie unter dem oberen Band, der Ring des Emblems, die Nummer und das Ablaufdatum, der Fotorahmen der Dienstausweise |
| `emblem` | Das Siegel: `star` (Standard), `shield`, `starOfLife` oder `wrench`. Bei Dienstausweisen auch das Wasserzeichen auf der Rückseite |
| `notice` | Der Text auf der Rückseite. Der Standard hängt von der Art ab |
| `word` | (`badge`) das Wort im Band unten, zum Beispiel `POLICE` |
| `authority` | (`badge`) der Titel unter der Unterschriftslinie auf der Rückseite, zum Beispiel `CHIEF OF POLICE` |
| `authorityName` | (`badge`) der Name, der auf dieser Linie unterschreibt, leer für keinen |

Farben sind Hex-Werte (`#1d4e89`). Halte `secondary` hell und `primary` dunkel: Die Daten stehen in dunkler Schrift auf dem Hintergrund, die Bänder haben weiße Schrift.

<Tip>
  Der Rang auf einem Dienstausweis ist das Job-Grade-Label des Inhabers zum Zeitpunkt der Ausstellung.
</Tip>

## Fälschen

Ein eigenes Dokument kann genauso gefälscht werden wie die mitgelieferten. Ab welcher Fälscherstufe, hängt von seiner Art ab, in `Config.Forging.levels` (`config/forgery.lua`): standardmäßig Ausweise ab der ersten Stufe, Lizenzen ab der zweiten und Dienstausweise ab der vierten. Siehe [Fälschen, Arbeiter und Aufträge](/de/jaksam-identity/guides/forging).
