---
title: "Hooks"
icon: "webhook"
description: "Intercepte et modifie le comportement de l'inventaire avec des hooks côté serveur pour les transferts, l'utilisation et la création d'items"
tag: "Updated"
---

Les hooks sont un moyen de modifier le comportement du système d'inventaire. Ils sont enregistrés sur le serveur et peuvent être utilisés pour modifier le comportement du système d'inventaire, par exemple pour empêcher les joueurs de déplacer des items vers un inventaire spécifique. Il y a des exemples de hooks dans le dossier `jaksam_inventory/_hooks`.

## Bonnes pratiques

<CardGroup cols={3}>
  <Card title="Utilise des filtres" icon="filter">
    Utilise toujours les filtres appropriés pour éviter des exécutions de hook inutiles
  </Card>

  <Card title="Sorties anticipées" icon="right-from-bracket">
    Utilise des sorties anticipées pour quitter les hooks quand les conditions ne sont pas remplies
  </Card>

  <Card title="Performance" icon="gauge-high">
    Garde la logique des hooks légère pour ne pas impacter les performances de l'inventaire
  </Card>
</CardGroup>

## Exemples de cas d'usage

- Empêcher les joueurs de voler des items ayant le champ de métadonnée `sole_owner` (par exemple, des items VIP)
- Empêcher les joueurs de déplacer des armes de police vers leur inventaire personnel
- N'autoriser qu'un seul sac à dos par inventaire de joueur
- Fabriquer des items en glissant un item spécifique sur un autre (par exemple glisser du pain sur de la viande pour faire un sandwich)
- Bloquer l'utilisation d'un item quand le joueur est menotté ou dans certaines zones
- Suivre les statistiques d'utilisation des items et les succès
- Empêcher l'utilisation de certains items en véhicule
- Ajouter des items de départ aux nouveaux inventaires de joueur lors de leur création
- Pré-remplir des poubelles ou planques avec des items aléatoires à leur création

## Fonctions de l'API

### Enregistrer un hook

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerHook(eventName, callback, options, priority)
```

</CodeGroup>

#### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `eventName` | string | Le nom de l'event de hook à écouter (voir [Events de hook disponibles](#available-hook-events) ci-dessous) |
| `callback` | function | La fonction à exécuter quand le hook est déclenché |
| `options` | table | Filtres et options de configuration (voir [Paramètre options](#options-parameter) ci-dessous) |
| `priority` | number | Priorité d'exécution (les nombres plus élevés s'exécutent en premier, par défaut : 0) |

#### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `hookId` | string | Identifiant unique du hook enregistré (utilisé pour désenregistrer le hook) |

### Désenregistrer un hook

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterHook(hookId)
```

</CodeGroup>

#### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `hookId` | string | L'identifiant unique retourné lors de l'enregistrement du hook |

### Désenregistrer tous les hooks d'une resource

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterResourceHooks(resourceName)
```

</CodeGroup>

#### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `resourceName` | string | Nom de la resource pour laquelle désenregistrer tous les hooks |

## Paramètre options

Le paramètre options accepte une table avec des filtres pour optimiser les performances.

<Tabs>
  <Tab title="Commun (tous les events)">
    ```lua
        local options = {
            -- Debug : affiche dans la console quand le hook se déclenche
            print = true,

            -- Ne se déclenche que pour des items spécifiques
            itemNameFilter = {
                bread = true,
                weapon_pistol = true
            },

            -- Ne se déclenche que pour des types d'items spécifiques
            itemTypeFilter = {
                weapon = true,
                currency = true
            }
        }
    ```
  </Tab>
  <Tab title="Filtres d'inventaire">
    Pour `onItemAdded`, `onItemRemoved`, `onInventoryCreated`, `onPreOpenInventory`, `onOmnipackTransaction` :

    ```lua
        local options = {
            -- Filtre par type d'inventaire (recommandé)
            inventoryTypeFilter = {
                player = true,
                stash = true
            },

            -- Filtre par motifs d'inventaire spécifiques (avancé)
            inventoryFilter = {
                "player:.*",      -- Tous les joueurs
                "stash_police"    -- Planque spécifique
            }
        }
    ```
  </Tab>
  <Tab title="Filtres de transfert">
    Pour `onItemTransferred` uniquement :

    ```lua
        local options = {
            -- Filtre l'inventaire source par type
            inventoryFromTypeFilter = { player = true },

            -- Filtre l'inventaire source par motif de nom
            inventoryFromFilter = {
                "player:.*",      -- Tous les joueurs
                "vehicle:123"     -- Véhicule spécifique
            },

            -- Filtre l'inventaire de destination par type
            inventoryToTypeFilter = { stash = true },

            -- Filtre l'inventaire de destination par motif de nom
            inventoryToFilter = {
                "stash_police",   -- Planque spécifique
                "container:.*"    -- Tous les containers
            },

            -- Uniquement les déplacements intra-inventaire (glisser dans le même inventaire)
            intraInventoryOnly = true
        }
    ```
  </Tab>
</Tabs>

## Events de hook disponibles

| Event | Description |
| --- | --- |
| [Item ajouté](/fr/jaksam-inventory/hooks/on-item-added) | Se déclenche quand un item est ajouté à un inventaire |
| [Item retiré](/fr/jaksam-inventory/hooks/on-item-removed) | Se déclenche quand un item est retiré d'un inventaire |
| [Item transféré](/fr/jaksam-inventory/hooks/on-item-transferred) | Se déclenche quand un item est transféré entre inventaires |
| [Transaction omnipack](/fr/jaksam-inventory/hooks/on-omnipack-transaction) | Se déclenche quand un admin crée ou détruit un item via l'inventaire admin |
| [Pre use item](/fr/jaksam-inventory/hooks/on-pre-use-item) | Se déclenche avant qu'un item soit utilisé, peut annuler l'utilisation |
| [Post use item](/fr/jaksam-inventory/hooks/on-post-use-item) | Se déclenche après qu'un item ait été utilisé, notification uniquement |
| [Inventaire créé](/fr/jaksam-inventory/hooks/on-inventory-created) | Se déclenche quand un nouvel inventaire est créé |
| [Pre open inventory](/fr/jaksam-inventory/hooks/on-pre-open-inventory) | Se déclenche avant l'ouverture d'un inventaire secondaire, peut empêcher son ouverture |

## Comportement des hooks

<CardGroup cols={2}>
  <Card title="Priorité" icon="arrow-up-1-9">
    Les nombres plus élevés s'exécutent en premier (par défaut : 0)
  </Card>

  <Card title="Valeurs de retour" icon="reply">
    `return nil` ou `return true` : autorise l'action à continuer.

    `return false, "message", "notifyType"` : empêche l'action et arrête l'exécution des hooks suivants. Les paramètres message et notifyType sont optionnels (notifyType peut être `"error"`, `"success"`, `"info"`)
  </Card>
</CardGroup>

<Note>
  **Exception - [`onPreOpenInventory`](/fr/jaksam-inventory/hooks/on-pre-open-inventory)** : le message n'est pas affiché au joueur, car le préchargement le ferait se répéter. Appelle `notifyPlayer` depuis l'intérieur du hook si tu veux expliquer la raison au joueur.
</Note>

## Compatibilité ox_inventory

Quand la ressource de compatibilité ox_inventory est installée, `exports.ox_inventory:registerHook(...)` est traduit vers les hooks natifs ci-dessus, les scripts ox_inventory fonctionnent donc sans modification. Les payloads sont remis au format ox, et les noms d'options ox (`itemFilter`, `typeFilter`, `inventoryFilter`, `print`) sont traduits également.

| Hook ox_inventory | Supporté | Hook natif utilisé |
| --- | --- | --- |
| `createItem` | Oui | `onItemAdded` |
| `swapItems` | Oui | `onItemTransferred` |
| `openInventory` | Oui | `onPreOpenInventory` |
| `usingItem` | Oui | `onPreUseItem` |
| `buyItem` / `openShop` | Non | pas encore de hooks de shop |
| `craftItem` | Non | pas encore de hooks de craft |

Enregistrer un hook non supporté affiche un avertissement et retourne `nil` au lieu de lever une erreur.

Trois différences à connaître lors de la migration :

- Un hook ox peut seulement autoriser ou bloquer ; il ne peut pas fournir de message personnalisé ni de type de notification. Utilise les hooks natifs pour cela
- `openInventory` hérite de l'exigence d'absence d'état décrite dans [`onPreOpenInventory`](/fr/jaksam-inventory/hooks/on-pre-open-inventory)
- **Les inventaires de joueur sont identifiés différemment.** Les hooks ox reçoivent l'ID serveur du joueur sous forme de number (`inventoryId = 4`), comme ox_inventory. Les hooks natifs reçoivent l'identifiant de personnage de jaksam sous forme de string (`inventoryId = "char1:35030084..."`). Tous les autres types d'inventaire utilisent le même ID string dans les deux cas
