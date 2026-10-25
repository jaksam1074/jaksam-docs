---
title: "Installation"
description: "Installe Boosting Creator sur ton serveur FiveM avec ESX, QBCore ou Qbox, ajoute l'item du laptop et donne la permission admin."
icon: "download"
---

Fais tourner **Boosting Creator** sur ton serveur FiveM.

## Prérequis

| Ressource | Pourquoi |
| --- | --- |
| `es_extended` **ou** `qb-core` / `qbx_core` | Framework |
| `ox_lib` | Callbacks et modules optionnels |
| `oxmysql` (ou `mysql-async`) | Base de données |
| OneSync | Les voitures des contrats, les gardes et les poursuivants sont des entités réseau |
| `vehicles_keys` (optionnel) | Crochetage et démarrage aux fils avec vehicles_keys, clés temporaires pour la voiture volée |
| `datacrack`, `utk_fingerprint`, `ultra-keypackhack` (optionnel) | Mini-jeux de piratage en plus |

<Warning>
  Les voitures des contrats, les gardes, les voitures du garage, le porte-voitures et le gang qui poursuit sont créés par le jeu du voleur et vérifiés par le serveur. Avec `sv_entityLockdown strict`, rien ne peut apparaître et chaque contrat est annulé juste après son début.
</Warning>

<Danger>
  N'utilise **PAS** FileZilla pour envoyer les fichiers, sinon le script **NE** fonctionnera **PAS**.

  Utilise [WinSCP](https://winscp.net/eng/download.php) à la place.
</Danger>

## Installer la ressource

Il y a une version pour **ESX** et une pour **QBCore et Qbox**. Prends celle de ton framework.

<Steps>
  <Step title="Télécharger Boosting Creator">
    Télécharge la version de ton framework et extrais le dossier `boosting_creator` dans le dossier `resources` de ton serveur.
  </Step>
  <Step title="Configurer le server.cfg">
    Démarre-le **après** tout ce dont il a besoin, par exemple :

    ```cfg
    ensure oxmysql
    ensure ox_lib
    ensure es_extended
    ensure vehicles_keys
    ensure boosting_creator
    ```
  </Step>
  <Step title="Base de données">
    Rien à faire : les tables sont créées au premier démarrage et les nouvelles colonnes sont ajoutées à chaque mise à jour.

    Les fichiers de `boosting_creator/sql/` servent uniquement pour les bases où le script n'a pas le droit de créer des tables.
  </Step>
  <Step title="Ajouter l'item du laptop">
    Les joueurs ouvrent le laptop de boosting avec un item, `boosting_laptop` par défaut. Voir [Item du laptop](#item-du-laptop) plus bas.
  </Step>
  <Step title="Donner la permission admin">
    Voir [Permission admin](#permission-admin) plus bas, puis ouvre le menu avec `/boostingcreator`.
  </Step>
</Steps>

## Item du laptop

Le nom de l'item se règle dans le menu, **Paramètres > Général > Nom de l'item laptop**. Le changer demande un redémarrage du script.

<Tabs>
  <Tab title="jaksam inventory">
    Rien à faire : l'item est créé automatiquement au démarrage, et à nouveau quand l'inventaire redémarre.

    Pour l'image de l'item, copie `boosting_creator/images/boosting_laptop.png` dans `jaksam_inventory_data/_images/`.
  </Tab>
  <Tab title="ox_inventory">
    Ajoute ceci dans `ox_inventory/data/items.lua` :

    ```lua
    ['boosting_laptop'] = {
        label = 'Boosting Laptop',
        weight = 1000,
        stack = false,
        close = true,
        description = 'Contracts for those who know where to look',
    },
    ```

    Le script écoute l'event d'utilisation propre à ox_inventory, pas besoin de `server.export`.

    Pour l'image de l'item, copie `boosting_creator/images/boosting_laptop.png` dans `ox_inventory/web/images/`.
  </Tab>
  <Tab title="ESX">
    Exécute ceci sur ta base de données :

    ```sql
    INSERT IGNORE INTO `items` (`name`, `label`, `weight`) VALUES ('boosting_laptop', 'Boosting Laptop', 1);
    ```
  </Tab>
  <Tab title="QBCore">
    Ajoute ceci dans `qb-core/shared/items.lua` :

    ```lua
    ['boosting_laptop'] = {['name'] = 'boosting_laptop', ['label'] = 'Boosting Laptop', ['weight'] = 1000, ['type'] = 'item', ['image'] = 'boosting_laptop.png', ['unique'] = true, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Contracts for those who know where to look'},
    ```

    Pour l'image de l'item, copie `boosting_creator/images/boosting_laptop.png` dans `qb-inventory/html/images/`.
  </Tab>
</Tabs>

<Info>
  Si l'item n'existe pas, la console du serveur l'indique en jaune au démarrage : `The item boosting_laptop doesn't exist, create it in your inventory to use the laptop`.
</Info>

## Permission admin

Le menu et chaque action admin vérifient un ace, `boostingcreator` par défaut (modifiable dans **Paramètres > Général**). L'ace `jaksam` fonctionne toujours aussi.

```cfg
add_ace group.admin boostingcreator allow
```

<Tip>
  Sans la permission, `/boostingcreator` ouvre une fenêtre avec les lignes `add_ace` exactes pour ta propre licence et ton compte Steam, prêtes à copier dans `server.cfg`.
</Tip>

## Vérification

Ouvre `/boostingcreator` (ou `/boostcreator`) en jeu. Si le menu s'ouvre avec les classes D à S déjà présentes, le script fonctionne correctement.

Ensuite, donne-toi le laptop, utilise-le et rejoins la file : la première offre arrive après 45 à 120 secondes avec les réglages par défaut.

## Mettre à jour

<Warning>
  Avant une mise à jour, sauvegarde `boosting_creator/current_config.json` (tous les réglages du menu) et le dossier `boosting_creator/integrations/`, puis remets-les dans la nouvelle version. Si tu remplaces le dossier sans eux, les réglages et les intégrations par défaut reviennent.
</Warning>

Les classes, les véhicules, les lieux, les fixers et les profils des joueurs sont dans la base de données et sont conservés. Voir aussi [Mettre à jour les scripts](/fr/jaksams-scripts/how-to-update-the-scripts).
