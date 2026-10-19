---
title: "Créer ton propre document"
description: "Ajoute à Jaksam Identity ta propre pièce d'identité, licence ou carte de service, étape par étape : l'item, le type de document, son apparence, où il est délivré et comment le tester."
icon: "pen-ruler"
---

Un document, ce sont deux choses : **un item dans ton inventaire** et **une entrée dans `Config.Documents`** (`config/documents.lua`). Cette page construit deux exemples de zéro :

- un **permis de chasse**, un document `license` délivré dans une mairie
- une **carte de service des pompiers**, un document `badge` pour le job `fire`

Les mêmes étapes valent pour n'importe quelle autre carte. Ce que les trois types signifient dans le registre est expliqué dans [Documents et registre](/fr/jaksam-identity/guides/documents-and-register).

## Choisir le type

| Type | Pour quoi | Le registre le dit valide tant que |
| --- | --- | --- |
| `identity` | Cartes d'identité, passeports, titres de séjour | le statut de l'enregistrement est valide |
| `license` | Tout ce qui repose sur une licence de ton framework | le statut est valide **et** le personnage a toujours la licence |
| `badge` | Cartes de service d'un job | le statut est valide **et** le titulaire a toujours le job |

## Étape par étape

<Steps>
  <Step title="Vérifier que la licence existe (license uniquement)">
    <Tabs>
      <Tab title="ESX">
        Le type de licence doit être une ligne de la table `licenses` d'esx_license. Si aucun autre script ne l'ajoute, ajoute-la toi-même :

        ```sql
        INSERT INTO licenses (type, label) VALUES ('hunting', 'Hunting licence');
        ```

        S'il manque, la console écrit au démarrage `hunting: licence type "hunting" is not in the licenses table`.
      </Tab>
      <Tab title="QBCore / Qbox">
        Rien à créer : la licence est la clé `hunting` dans les métadonnées du personnage `licences`. Le script connaît tous les types de licence qu'un document utilise.
      </Tab>
    </Tabs>
  </Step>

  <Step title="Ajouter l'item">
    Le nom de l'item est libre, il doit seulement correspondre à `item` à l'étape suivante. Donne-lui une image au nom de l'item (par exemple `hunting_license.webp`) dans le dossier d'images de ton inventaire.

    <Tabs>
      <Tab title="jaksam_inventory">
        Ajoute-le à `jaksam_inventory_data/items.lua`. `type = 'idcards'` lui donne les actions du clic droit **View**, **Show** et **Copy number**, `onUse` le passe au script et `dynamicMetadata` remplit un document qui vient d'un shop ou d'un give admin :

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

        - Une licence avec des **catégories** a aussi besoin de `classes = { metadataTemplateId = 'doc_classes', onlyFirstAdd = true }`
        - Une **carte de service** a aussi besoin de `rank = { metadataTemplateId = 'doc_rank', onlyFirstAdd = true }`

        Redémarre `jaksam_inventory` une fois.
      </Tab>
      <Tab title="ox_inventory">
        Ajoute-le à `ox_inventory/data/items.lua`. Les données des documents de shops et de gives admin viennent du script, pas besoin de métadonnées ici :

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
        Ajoute-le à `qb-core/shared/items.lua`. Le script gère son utilisation dès que l'item figure dans `Config.Documents` :

        ```lua
        hunting_license = { name = 'hunting_license', label = 'Hunting licence', weight = 10, type = 'item', image = 'hunting_license.webp', unique = true, useable = true, shouldClose = true, description = 'Permit to hunt' },
        ```
      </Tab>
    </Tabs>
  </Step>

  <Step title="Ajouter le type de document">
    Une entrée dans `Config.Documents`. La clé (`hunting`, `badge_fd`) est le **type de document** : elle est enregistrée dans le registre et utilisée par les mairies, les commandes et les exports. Ne la renomme pas une fois que des documents de ce type existent.

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

    | Champ | Description |
    | --- | --- |
    | `item` | L'item de l'étape précédente |
    | `kind` | `identity`, `license` ou `badge` |
    | `license` | (`license`) le type de licence |
    | `licenses` | (`license`, à la place de `license`) plusieurs types de licence imprimés comme catégories, par exemple `{ boat_small = 'A', boat_large = 'B' }` |
    | `job` | (`badge`) le job auquel la carte de service appartient |
    | `label` | Nom dans les menus et les mairies. Un texte simple ou une clé de locale avec `L('...')` |
    | `validityDays` | Jours avant expiration, `nil` pour jamais |
    | `layout` | `id` (carte horizontale, par défaut) ou `badge` (carte de service verticale) |
    | `theme` | L'apparence, voir [L'apparence de la carte](#lapparence-de-la-carte) |
  </Step>

  <Step title="Décider qui le délivre">
    <Tabs>
      <Tab title="identity / license">
        Ajoute le type aux `documents` d'une mairie et donne-lui ses frais dans `Config.Offices` (`config/office.lua`), ou sur la page des mairies de `/documents config` :

        ```lua
        fees = {
            hunting = { first = 300, renew = 120, replace = 350 },
        },
        locations = {
            { label = 'Ranger station', coords = vec4(0.0, 0.0, 0.0, 0.0), model = 's_m_y_ranger_01', documents = { 'hunting' } },
        },
        ```

        Sans une mairie qui le propose, le document existe mais **aucun guichet ne le délivre**. Une licence n'est délivrée qu'aux personnages qui la possèdent : la mairie ne l'accorde pas.

        Un document `identity` peut aussi aller à chaque nouveau personnage : ajoute le type à `Config.Starter.documents`. Voir [Mairies](/fr/jaksam-identity/guides/citizen-offices).
      </Tab>
      <Tab title="badge">
        Les cartes de service ne sont jamais délivrées dans une mairie. Délivre-les avec la commande admin, ou depuis ton propre menu de patron avec l'export `Issue` :

        ```lua
        local serial, reason = exports["jksm_identity"]:Issue(employeeId, "badge_fd", { issuerSrc = bossId })
        ```

        L'employé doit avoir le job de la carte, sinon `reason` vaut `wrong_job`. Pour limiter qui peut la délivrer, utilise le [hook CanIssue](/fr/jaksam-identity/server/hooks/can-issue). Voir [Délivrer](/fr/jaksam-identity/server/register/issue).
      </Tab>
    </Tabs>
  </Step>

  <Step title="Redémarrer et tester">
    Redémarre `jksm_identity`, puis en jeu :

    ```bash
    /documents issue <your id> hunting grant    # grant gives the licence first
    /documents issue <your id> badge_fd force   # force skips the job check
    ```

    Utilise l'item pour le regarder, et vérifie-le avec `/documents check <serial>`.
  </Step>
</Steps>

## L'apparence de la carte

Tous les champs de `theme` sont facultatifs.

| Champ | Où il apparaît |
| --- | --- |
| `header` | Petite ligne en haut. Par défaut `STATE OF SAN ANDREAS` |
| `title` | Grand titre au recto (sur les cartes de service aussi au verso). Par défaut le `label` en majuscules |
| `primary` | La bande colorée en haut, la bande du mot des cartes de service et l'intérieur de l'emblème. Aussi la couleur du document dans le [portefeuille du téléphone](/fr/jaksam-identity/guides/roadphone-wallet) |
| `secondary` | Le fond de la carte |
| `accent` | La ligne sous la bande du haut, l'anneau de l'emblème, le numéro et la date d'expiration, le cadre de la photo des cartes de service |
| `emblem` | Le sceau : `star` (par défaut), `shield`, `starOfLife` ou `wrench`. Sur les cartes de service aussi le filigrane au verso |
| `notice` | Le texte au verso. Celui par défaut dépend du type |
| `word` | (`badge`) le mot dans la bande du bas, par exemple `POLICE` |
| `authority` | (`badge`) le titre sous la ligne de signature au verso, par exemple `CHIEF OF POLICE` |
| `authorityName` | (`badge`) le nom qui signe sur cette ligne, vide pour aucun |

Les couleurs sont des valeurs hex (`#1d4e89`). Garde un `secondary` clair et un `primary` foncé : les données sont imprimées en texte foncé sur le fond, les bandes ont un texte blanc.

<Tip>
  Le grade sur une carte de service est le libellé du grade de job du titulaire au moment où elle a été délivrée.
</Tip>

## Le contrefaire

Un document personnalisé se contrefait comme ceux fournis. À partir de quel niveau de faussaire dépend de son type, dans `Config.Forging.levels` (`config/forgery.lua`) : par défaut les pièces d'identité dès le premier niveau, les licences dès le deuxième et les cartes de service dès le quatrième. Voir [Contrefaçon, ouvriers et commandes](/fr/jaksam-identity/guides/forging).
