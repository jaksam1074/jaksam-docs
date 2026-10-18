---
title: "Installation"
description: "Installe Jaksam Identity sur ton serveur FiveM avec ESX, QBCore ou Qbox, ajoute les items à ton inventaire et configure les premières mairies et ateliers."
icon: "download"
---

Fais tourner **Jaksam Identity** sur ton serveur FiveM.

## Prérequis

| Ressource | Pourquoi |
| --- | --- |
| `es_extended` (avec les tables esx_license) **ou** `qb-core` / `qbx_core` | Framework |
| `jaksam_inventory` 1.28 ou plus récent, **ou** `ox_inventory`, **ou** `qb-inventory` 2.2 (version QBCore uniquement) | Les documents sont des items avec des données |
| `ox_lib`, `oxmysql` | Callbacks, menus, base de données |
| `ox_target` **ou** `qb-target` (version QBCore uniquement) | Targets |
| `bob74_ipl` | L'intérieur de l'atelier de faussaire |
| RoadPhone (optionnel) | Numéros de téléphone sur les cartes de visite, [portefeuille du téléphone](/fr/jaksam-identity/guides/roadphone-wallet) |
| `esx_dmvschool` (optionnel, ESX uniquement) | Le premier permis de conduire est délivré après l'examen |

<Warning>
  Le script crée et met à jour ses propres tables au démarrage. **Sauvegarde ta base de données** avant l'installation et avant chaque mise à jour.
</Warning>

## Installer la ressource

Il y a une version pour **ESX** et une pour **QBCore et Qbox** (elle détecte elle-même lequel des deux tourne). Prends celle de ton framework.

<Tabs>
  <Tab title="ESX" icon="server">
    <Steps>
      <Step title="Télécharger Jaksam Identity">
        Télécharge la version ESX et extrais le dossier `jksm_identity` dans le dossier `resources` de ton serveur.
      </Step>
      <Step title="Configurer le server.cfg">
        Démarre-le **après** tout ce dont il a besoin, par exemple :

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
      <Step title="Base de données">
        Rien à faire : les tables sont créées et mises à jour au démarrage (`jksm_identity_schema` garde la version).

        `install/install.sql` sert uniquement pour les bases où le script n'a pas le droit de créer des tables.
      </Step>
      <Step title="Ajouter les items">
        Ajoute les items à ton inventaire, voir [Installer les items](#installer-les-items) plus bas.
      </Step>
      <Step title="config/main.lua">
        - `Config.Bridge` : inventaire (`'jaksam'` ou `'ox_inventory'`), notifications (`'esx'` ou `'ox_lib'`), téléphone (`'roadphone'` ou `'none'`) et menus
        - `Config.Locale` : `'en'` ou `'de'`
        - `Config.AdminGroups` / `Config.AdminAce` : qui peut utiliser la commande admin
        - `Config.Debug = false` sur un serveur en production
      </Step>
    </Steps>

    <Warning>
      **esx_dmvschool :** son event `esx_dmvschool:addLicense` n'est pas vérifié côté serveur, un client tricheur peut donc s'attribuer n'importe quelle licence avec. Jaksam Identity fait confiance aux licences de la base et, avec `Config.DmvSchool` actif, délivre le permis de conduire après cet event. Sécurise l'event dans esx_dmvschool, ou mets `Config.DmvSchool.enabled = false`, sur un serveur en production.
    </Warning>
  </Tab>
  <Tab title="QBCore / Qbox" icon="server">
    <Steps>
      <Step title="Télécharger Jaksam Identity">
        Télécharge la version QBCore et extrais le dossier `jksm_identity` dans le dossier `resources` de ton serveur.
      </Step>
      <Step title="Retirer qbx_idcard (Qbox)">
        Jaksam Identity prend sa place : il répond au nom `qbx_idcard`, à ses exports `GetMetaLicense` et `CreateMetaLicense` et à son event d'affichage, donc les items de départ de qbx_core et qbx_cityhall continuent de fonctionner sans changement.

        <Warning>
          Si `qbx_idcard` tourne encore, deux cartes s'ouvriront.
        </Warning>
      </Step>
      <Step title="Configurer le server.cfg">
        Démarre-le **après** tout ce dont il a besoin, par exemple :

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
      <Step title="Base de données">
        Rien à faire : les tables sont créées et mises à jour au démarrage (`jksm_identity_schema` garde la version).

        `install/install.sql` sert uniquement pour les bases où le script n'a pas le droit de créer des tables.
      </Step>
      <Step title="Ajouter les items">
        Ajoute les items à ton inventaire, voir [Installer les items](#installer-les-items) plus bas.
      </Step>
      <Step title="config/main.lua">
        - `Config.Bridge.framework = 'auto'` détecte si c'est qb-core ou qbx_core qui tourne
        - `Config.Bridge.target = 'auto'` utilise ox_target s'il est installé, sinon qb-target
        - `Config.Bridge.inventory` : `'jaksam'`, `'ox_inventory'` ou `'qb-inventory'`
        - `Config.Locale` : `'en'` ou `'de'`
        - `Config.AdminGroups` / `Config.AdminAce` : qui peut utiliser la commande admin
        - `Config.Debug = false` sur un serveur en production
      </Step>
    </Steps>

    <Info>
      - **Items :** la carte d'identité, le permis de conduire et le permis de port d'arme sont les items QBCore `id_card`, `driver_license` et `weaponlicense`. Les cartes de service, les cartes de visite et le matériel de l'atelier sont des items de ce script.
      - **Items de départ et mairie :** ce que donnent qb-core, qbx_core et qb-cityhall / qbx_cityhall devient un document enregistré du personnage. qbx_cityhall le délivre avec une photo prise sur place.
      - **Anciens champs de carte :** chaque carte porte aussi `citizenid`, `birthdate`, `nationality` et `cardtype` pour les scripts qui les lisent.
      - **Les licences** viennent des métadonnées du personnage `licences` (`driver` est le `drive` du script).
      - **Argent sale :** sur QBCore l'item `markedbills` (sa valeur dans `metadata.worth`), sur Qbox l'item empilable `black_money`.
      - La prise en charge d'esx_dmvschool n'existe que dans la version ESX.
    </Info>
  </Tab>
</Tabs>

## Installer les items

<Tabs>
  <Tab title="jaksam_inventory" icon="boxes-stacked">
    <Steps>
      <Step title="Ajouter les entrées des items">
        Ajoute les entrées de `install/jaksam_items.lua` dans `jaksam_inventory_data/items.lua`, dans la table après `return { }`.
      </Step>
      <Step title="Ajouter les types d'items">
        Copie `install/jaksam_item_types.lua` tel quel vers `jaksam_inventory_data/_data/jksm_identity.lua`. Il ajoute les actions du clic droit **View**, **Show** et **Copy number**. Rien à coller : les fichiers de ce dossier survivent aux mises à jour de l'inventaire.
      </Step>
      <Step title="Copier les images">
        Copie `install/images/*.webp` vers `jaksam_inventory_data/_images/`.
      </Step>
      <Step title="Redémarrer l'inventaire">
        Redémarre `jaksam_inventory` une fois.
      </Step>
    </Steps>

    Voir [Items des boutiques ou des admins](#items-des-boutiques-ou-des-admins) pour le bloc de métadonnées que chaque item de document doit garder.
  </Tab>
  <Tab title="ox_inventory" icon="box">
    Mets `Config.Bridge.inventory = 'ox_inventory'` et `Config.InventoryKeys = { 'TAB' }` (la touche qui ouvre l'inventaire à côté d'une carte ouverte).

    <Steps>
      <Step title="Ajouter les items">
        Ajoute `install/ox_items.lua` dans `ox_inventory/data/items.lua`.
      </Step>
      <Step title="Copier les images">
        Copie `install/images/*.webp` vers `ox_inventory/web/images/`.
      </Step>
    </Steps>

    - Les documents reçoivent un export d'utilisation (montrer ou regarder, `Config.UseAction`) et les boutons du clic droit **View** et **Show**. Copier le numéro, c'est le "Copy serial number" propre à ox_inventory.
    - **Les documents des boutiques et des admins** reçoivent leurs données du script via le hook `createItem` d'ox, sans métadonnées dans les définitions des items.
    - **Les piles d'ID** sont des conteneurs ox, créés par le script. Un portefeuille ne compte pour le portefeuille du téléphone que s'il est un conteneur ox (`setContainerProperties`) listé dans `Config.WalletContainers`. ox n'autorise pas un conteneur dans un autre conteneur.
    - **Les documents au sol** peuvent être consultés par celui qui a ouvert ce drop.
  </Tab>
  <Tab title="qb-inventory" icon="box-open">
    Version QBCore uniquement, faite pour **qb-inventory 2.2**. Mets `Config.Bridge.inventory = 'qb-inventory'` et `Config.InventoryKeys = { 'TAB' }`.

    <Steps>
      <Step title="Ajouter les items">
        Ajoute `install/qb_items.lua` dans `qb-core/shared/items.lua`, en remplaçant les trois items de carte que QBCore a déjà.
      </Step>
      <Step title="Copier les images">
        Copie `install/images/*.webp` vers `qb-inventory/html/images/`.
      </Step>
    </Steps>

    Rien à modifier dans qb-inventory, et sa propre carte d'identité dans le chat n'apparaît plus.

    - **Utiliser un document** le montre ou l'ouvre (`Config.UseAction`). qb-inventory n'a pas de boutons de clic droit, mets donc `Config.UseAction = 'menu'` pour choisir à chaque fois entre regarder et montrer. Une carte de visite demande toujours (regarder, montrer, donner). Le numéro se copie depuis la carte ouverte.
    - **Les documents des items de départ, de la mairie, d'une boutique ou de `/giveitem`** reçoivent leurs données du script (hook `ItemAdded` de qb-inventory).
    - **Pas de piles d'ID :** qb-inventory n'a pas de conteneurs. Les documents d'une commande arrivent un par un dans le stockage des résultats, et le portefeuille du téléphone ne lit que l'inventaire principal.
    - **Un stockage n'est ouvert que pour un joueur à la fois** (règle de qb-inventory). Ce que les ouvriers y mettent pendant qu'il est ouvert apparaît en le rouvrant.

    <Warning>
      **Documents scellés :** qb-inventory reprend les données d'un item depuis le client quand un joueur le donne ou le jette. Chaque document porte donc un sceau fait avec une clé que seul le serveur connaît (table `jksm_identity_settings`, créée au premier démarrage). Un document aux données inventées ou modifiées n'a pas de sceau valide : il n'affiche rien et le dit. **Garde cette table quand tu déplaces la base de données**, sinon les documents des inventaires perdent leur sceau.
    </Warning>
  </Tab>
</Tabs>

### Items des boutiques ou des admins

Quand le script délivre un document, il passe lui-même les métadonnées. Quand un item de document apparaît autrement (une boutique jaksam, un don d'admin), les modèles de métadonnées le remplissent. Les entrées de `install/jaksam_items.lua` ont déjà ce bloc, garde-le sur chaque item de document :

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

Les modèles sont enregistrés au démarrage et à nouveau à chaque redémarrage de jaksam_inventory. Un document créé par un modèle est **enregistré** (authentique), sauf si sa `rarity` jaksam est listée dans `Config.UnregisteredRarities` (par défaut `illegal`).

## Configurer

<Steps>
  <Step title="config/documents.lua">
    Les types de documents, leurs items, leur validité et leurs thèmes. Toute licence connue de ton framework peut devenir un document : ajoute l'item et une entrée ici. Voir [Documents et registre](/fr/jaksam-identity/guides/documents-and-register).
  </Step>
  <Step title="config/office.lua">
    Les documents de départ (`Config.Starter`, par défaut la carte d'identité) et les mairies (`Config.Offices`) : lieux, modèles de PNJ, documents gérés par chaque mairie, frais, espèces ou banque. Voir [Mairies](/fr/jaksam-identity/guides/citizen-offices).
  </Step>
  <Step title="config/forgery.lua">
    Liste les ateliers de faussaires dans `Config.Forgery.workshops` (entrée à l'extérieur, prix, jobs qui peuvent le posséder), ou ajoute-les en jeu avec `/documents config`. **Aucun atelier n'est configuré de base** : le côté contrefaçon reste invisible tant que tu n'en ajoutes pas un. Voir [Ateliers de faussaires](/fr/jaksam-identity/guides/forgery-workshops).
  </Step>
  <Step title="config/raid.lua">
    Les unités qui font des descentes dans les ateliers (tes jobs de police, à partir de quel grade) et l'emplacement de la salle des scellés de chaque unité. Sans salle des scellés, rien ne peut être saisi. `Config.Raid.enabled = false` désactive les descentes. Voir [Descentes](/fr/jaksam-identity/guides/raids).
  </Step>
</Steps>

<Tip>
  La plupart de ces réglages, lieux compris, se changent en jeu avec `/documents config`, sans modifier de fichier ni redémarrer. Voir [Réglages en jeu](/fr/jaksam-identity/guides/settings-in-game).
</Tip>

## Vérification

Démarre le serveur et lis la console. Une ressource manquante ou un bridge sans fichier est indiqué en rouge. **Aucune ligne rouge signifie que les vérifications de démarrage sont passées** (avec `Config.Debug = true`, il affiche aussi `start checks passed`).

En jeu, ouvre `/documents` en tant qu'admin : sans sous-commande, il liste toutes celles disponibles.
