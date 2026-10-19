---
title: "Create a custom document"
description: "Add your own ID card, licence or badge to Jaksam Identity, step by step: the item, the document type, its look, where it is issued, and how to test it."
icon: "pen-ruler"
---

A document is two things: **one item in your inventory** and **one entry in `Config.Documents`** (`config/documents.lua`). This page builds two examples from scratch:

- a **hunting licence**, a `license` document issued at a citizen office
- a **fire department badge**, a `badge` document for the job `fire`

The same steps work for any other card. For what the three kinds mean in the register, see [Documents and register](/jaksam-identity/guides/documents-and-register).

## Pick the kind

| Kind | Use it for | The register says valid while |
| --- | --- | --- |
| `identity` | ID cards, passports, residence permits | the record status is valid |
| `license` | Anything backed by a licence of your framework | the status is valid **and** the character still holds the licence |
| `badge` | Service IDs of a job | the status is valid **and** the owner still holds the job |

## Step by step

<Steps>
  <Step title="Make sure the licence exists (license only)">
    <Tabs>
      <Tab title="ESX">
        The licence type must be a row of the esx_license `licenses` table. If no other script adds it, add it yourself:

        ```sql
        INSERT INTO licenses (type, label) VALUES ('hunting', 'Hunting licence');
        ```

        If it is missing, the console prints `hunting: licence type "hunting" is not in the licenses table` on start.
      </Tab>
      <Tab title="QBCore / Qbox">
        Nothing to create: the licence is the key `hunting` in the character metadata `licences`. Every licence type a document uses is known to the script.
      </Tab>
    </Tabs>
  </Step>

  <Step title="Add the item">
    The item name is free, it only has to match `item` in the next step. Give it an image named after the item (for example `hunting_license.webp`) in your inventory's image folder.

    <Tabs>
      <Tab title="jaksam_inventory">
        Add it to `jaksam_inventory_data/items.lua`. `type = 'idcards'` gives it the right-click actions **View**, **Show** and **Copy number**, `onUse` hands it to the script and `dynamicMetadata` fills a document that comes from a shop or an admin give:

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

        - A licence with **classes** also needs `classes = { metadataTemplateId = 'doc_classes', onlyFirstAdd = true }`
        - A **badge** also needs `rank = { metadataTemplateId = 'doc_rank', onlyFirstAdd = true }`

        Restart `jaksam_inventory` once.
      </Tab>
      <Tab title="ox_inventory">
        Add it to `ox_inventory/data/items.lua`. The data of shop and admin-given documents comes from the script, no metadata needed here:

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
        Add it to `qb-core/shared/items.lua`. Using it is handled by the script as soon as the item is listed in `Config.Documents`:

        ```lua
        hunting_license = { name = 'hunting_license', label = 'Hunting licence', weight = 10, type = 'item', image = 'hunting_license.webp', unique = true, useable = true, shouldClose = true, description = 'Permit to hunt' },
        ```
      </Tab>
    </Tabs>
  </Step>

  <Step title="Add the document type">
    One entry in `Config.Documents`. The key (`hunting`, `badge_fd`) is the **document type**: it is stored in the register and used by the offices, the commands and the exports. Do not rename it once documents of that type exist.

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

    | Field | Description |
    | --- | --- |
    | `item` | The item from the previous step |
    | `kind` | `identity`, `license` or `badge` |
    | `license` | (`license`) the licence type |
    | `licenses` | (`license`, instead of `license`) several licence types printed as classes, for example `{ boat_small = 'A', boat_large = 'B' }` |
    | `job` | (`badge`) the job the badge belongs to |
    | `label` | Name in menus and offices. A plain string or a locale key with `L('...')` |
    | `validityDays` | Days until it expires, `nil` for never |
    | `layout` | `id` (landscape card, default) or `badge` (portrait service ID) |
    | `theme` | The look, see [The look of the card](#the-look-of-the-card) |
  </Step>

  <Step title="Decide who issues it">
    <Tabs>
      <Tab title="identity / license">
        Add the type to the `documents` of an office and give it its fees in `Config.Offices` (`config/office.lua`), or on the office page of `/documents config`:

        ```lua
        fees = {
            hunting = { first = 300, renew = 120, replace = 350 },
        },
        locations = {
            { label = 'Ranger station', coords = vec4(0.0, 0.0, 0.0, 0.0), model = 's_m_y_ranger_01', documents = { 'hunting' } },
        },
        ```

        Without an office that lists it, the document exists but **no counter hands it out**. A licence is only issued to characters who hold it: the office does not grant it.

        An `identity` document can also go to every new character: add the type to `Config.Starter.documents`. See [Citizen offices](/jaksam-identity/guides/citizen-offices).
      </Tab>
      <Tab title="badge">
        Badges are never issued at an office. Issue them with the admin command, or from your own boss menu with the `Issue` export:

        ```lua
        local serial, reason = exports["jksm_identity"]:Issue(employeeId, "badge_fd", { issuerSrc = bossId })
        ```

        The employee must have the job of the badge, otherwise `reason` is `wrong_job`. To limit who may issue it, use the [CanIssue hook](/jaksam-identity/server/hooks/can-issue). See [Issue](/jaksam-identity/server/register/issue).
      </Tab>
    </Tabs>
  </Step>

  <Step title="Restart and test">
    Restart `jksm_identity`, then in game:

    ```bash
    /documents issue <your id> hunting grant    # grant gives the licence first
    /documents issue <your id> badge_fd force   # force skips the job check
    ```

    Use the item to look at it, and check it with `/documents check <serial>`.
  </Step>
</Steps>

## The look of the card

Every field of `theme` is optional.

| Field | Where it shows |
| --- | --- |
| `header` | Small line at the top. Default `STATE OF SAN ANDREAS` |
| `title` | Big title on the front (on badges also on the back). Default the `label` in capitals |
| `primary` | The coloured band at the top, the word band of badges and the inside of the emblem. Also the colour of the document in the [phone wallet](/jaksam-identity/guides/roadphone-wallet) |
| `secondary` | The background of the card |
| `accent` | The line under the top band, the emblem ring, the number and the expiry date, the photo frame of badges |
| `emblem` | The seal: `star` (default), `shield`, `starOfLife` or `wrench`. On badges it is also the watermark on the back |
| `notice` | The text on the back. The default depends on the kind |
| `word` | (`badge`) the word in the band at the bottom, for example `POLICE` |
| `authority` | (`badge`) the title under the signature line on the back, for example `CHIEF OF POLICE` |
| `authorityName` | (`badge`) the name signed on that line, empty for none |

Colours are hex values (`#1d4e89`). Keep `secondary` light and `primary` dark: the data is printed in dark text on the background, the bands have white text.

<Tip>
  The rank on a badge is the job grade label of the owner when it was issued.
</Tip>

## Forging it

A custom document can be forged like the shipped ones. Which forger level may forge it depends on its kind, in `Config.Forging.levels` (`config/forgery.lua`): out of the box ID cards from the first level, licences from the second and badges from the fourth. See [Forging](/jaksam-identity/guides/forging).
