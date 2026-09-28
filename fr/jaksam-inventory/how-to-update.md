---
title: "Comment faire"
icon: "rectangle-new"
tag: "Update"
description: "Garde ton installation de Jaksam Inventory à jour sans perdre tes items personnalisés, paramètres, intégrations ou autres personnalisations."
---

# Mettre à jour Jaksam Inventory

Depuis la version **1.28**, la mise à jour est beaucoup plus simple : tout ce que tu modifies vit dans son propre dossier, donc une mise à jour consiste simplement à remplacer un dossier. Choisis le guide qui correspond à la version installée actuellement :

<CardGroup cols={3}>
  <Card title="1.28 et plus récentes" icon="bolt">
    Remplace un dossier, rien à sauvegarder ni à restaurer.
  </Card>

  <Card title="De 1.27 ou plus ancienne vers 1.28" icon="right-left">
    Une seule fois : tes personnalisations sont déplacées automatiquement.
  </Card>

  <Card title="Versions avant 1.28" icon="clock-rotate-left">
    L'ancien guide, pour les installations encore en 1.27 ou plus ancienne.
  </Card>
</CardGroup>

<Tip>
  Tu peux voir ta version installée dans `jaksam_inventory/fxmanifest.lua`, sur la ligne `version`.
</Tip>

## Version 1.28 et plus récentes

Tout ce que tu modifies (paramètres, items, images, hooks, modules, traductions, intégrations) est enregistré dans **`jaksam_inventory_data`**, un dossier à côté de `jaksam_inventory`. Les mises à jour remplacent uniquement `jaksam_inventory`, donc tes modifications ne sont jamais touchées.

<Steps>
  <Step title="Arrête ton serveur">
    Arrête ton serveur FiveM avant de remplacer les fichiers.
  </Step>
  <Step title="Remplace jaksam_inventory">
    Supprime le dossier `jaksam_inventory` et mets le nouveau à sa place. Laisse `jaksam_inventory_data` exactement où il est.
  </Step>
  <Step title="Démarre ton serveur">
    C'est tout : tes items, paramètres et personnalisations sont toujours là.
  </Step>
</Steps>

<Tip>
  Sauvegarder `jaksam_inventory_data` de temps en temps reste une bonne idée : c'est le seul dossier qui contient tout ton travail.
</Tip>

<Warning>
  **Ne modifie pas les fichiers dans `jaksam_inventory`**, chaque mise à jour les remplace. Si tu le fais, la console du serveur t'indique au démarrage quel fichier a été modifié et où cette modification doit aller dans `jaksam_inventory_data`. Les versions fournies de chaque fichier sont dans `jaksam_inventory/defaults` : lis-les, copie ce dont tu as besoin, mais ne les modifie pas.
</Warning>

### Ce que contient jaksam_inventory_data

| Fichier / Dossier | Contenu |
| --- | --- |
| `current_config.json` | Les paramètres du menu `/inventory` |
| `items.lua` | Tes nouveaux items, et seulement les champs que tu as modifiés sur les items par défaut. Le menu admin écrit aussi ici |
| `_images/` | Les images de tes items, nommées comme l'item (`bread.png`, `bread.webp`) |
| `variables.css` | Les couleurs par défaut de l'inventaire. Se définit depuis le menu des thèmes, ou en collant la sortie de la commande F8 `admintheme` |
| `locales/` | Seulement les textes que tu as modifiés |
| `integrations/` | Seulement les fonctions d'intégration que tu as modifiées |
| `_hooks/` | Tes hooks. Un fichier portant le même nom qu'un hook par défaut le remplace |
| `_modules/` | Tes modules. Le même chemin qu'un module par défaut le remplace |
| `_data/` | Fichiers exécutés après les `_data` par défaut, comme la taille des coffres de véhicules |
| `components.json` | Composants d'armes modifiés depuis le menu admin |
| `_backups/` | Une copie de `items.lua` avant chaque modification faite depuis le menu admin |

<Note>
  `jaksam_inventory_data` n'a besoin d'aucune ligne dans `server.cfg` : `jaksam_inventory` le démarre tout seul.
</Note>

### Dépannage

<AccordionGroup>
  <Accordion title="La console dit que jaksam_inventory_data est manquant">
    `jaksam_inventory_data` doit être à côté de `jaksam_inventory`, dans le même dossier. Remets le tien (ou restaure-le depuis ta sauvegarde) et redémarre le serveur. Si tu n'en as jamais eu, un dossier vide a été créé pour toi : redémarre simplement.
  </Accordion>

  <Accordion title="La console me demande de mettre à jour jaksam_core">
    Ton `jaksam_core` est trop ancien pour lire les paramètres depuis `jaksam_inventory_data`. Télécharge le dernier `jaksam_core` et remplace-le. En attendant, tes paramètres continuent de fonctionner depuis leur ancien emplacement.
  </Accordion>

  <Accordion title="La console dit qu'un fichier de jaksam_inventory a été modifié">
    Cette modification sera perdue à la prochaine mise à jour. Déplace-la à l'endroit indiqué par la console, dans `jaksam_inventory_data`.
  </Accordion>
</AccordionGroup>

## Passer de 1.27 ou plus ancienne à 1.28

Tu ne le fais qu'une seule fois. Ensuite, chaque mise à jour est la version simple ci-dessus.

<Steps>
  <Step title="Arrête ton serveur et fais une sauvegarde">
    Arrête ton serveur et fais une copie de tout ton dossier `jaksam_inventory`.
  </Step>
  <Step title="Mets aussi à jour jaksam_core">
    Télécharge le dernier `jaksam_core` et remplace le tien. Les anciennes versions ne peuvent pas lire les paramètres depuis leur nouvel emplacement.
  </Step>
  <Step title="Copie la nouvelle version par-dessus l'ancienne">
    Copie le nouveau `jaksam_inventory` **par-dessus** l'actuel, en écrasant les fichiers, et mets `jaksam_inventory_data` du téléchargement à côté.

    Ne supprime pas l'ancien dossier avant : tes anciens fichiers doivent encore être dans `jaksam_inventory` au premier démarrage pour pouvoir être déplacés. Si tu l'as déjà supprimé, copie `current_config.json`, `_data/`, `_hooks/`, `_modules/`, `integrations/`, `locales/` et tes images personnalisées de `_images/` depuis ta sauvegarde dans le nouveau `jaksam_inventory` avant de démarrer.
  </Step>
  <Step title="Démarre ton serveur">
    Au premier démarrage, tes paramètres, items, hooks, modules, intégrations, traductions et images personnalisées sont importés automatiquement dans `jaksam_inventory_data`. La console du serveur et le menu `/inventory` affichent ce qui a été importé, et les anciens fichiers sont déplacés dans `jaksam_inventory/_migrated`.
  </Step>
</Steps>

<Note>
  Deux choses ne sont pas déplacées automatiquement :

  - **Les couleurs personnalisées** de `dist/assets/variables.css` : ouvre le menu des thèmes et définis ton thème comme thème par défaut du serveur, ou copie les variables que tu as modifiées dans `jaksam_inventory_data/variables.css`
  - **Les traductions personnalisées du menu** dans `dist/menu_translations/` : elles restent dans `jaksam_inventory`, donc recopie-les après chaque mise à jour
</Note>

## Versions avant 1.28

<Info>
  Voici le guide pour les installations encore en version 1.27 ou plus ancienne, où tes personnalisations se trouvent dans le dossier `jaksam_inventory` lui-même.
</Info>

<Warning>
  **Crée toujours une sauvegarde avant de mettre à jour.** Ne supprime jamais ton installation existante avant d'avoir une sauvegarde fonctionnelle.
</Warning>

### Avant de commencer

<Tip>
  **Recommandé :** Garde ta sauvegarde pendant au moins quelques jours après la mise à jour. Cela facilite un retour en arrière si quelque chose ne va pas.
</Tip>

<CardGroup cols={2}>
  <Card title="Arrête ton serveur" icon="server">
    Arrête toujours ton serveur FiveM avant de remplacer les fichiers de l'inventaire.
  </Card>

  <Card title="Crée une sauvegarde" icon="floppy-disk">
    Sauvegarde tes fichiers et dossiers personnalisés avant d'installer la nouvelle version.
  </Card>

  <Card title="Installe la mise à jour" icon="download">
    Retire l'ancienne version et upload la dernière version de Jaksam Inventory.
  </Card>

  <Card title="Restaure tes personnalisations" icon="rotate">
    Restaure tes fichiers sauvegardés dans la nouvelle installation.
  </Card>
</CardGroup>

### Que dois-je sauvegarder ?

#### Toujours sauvegarder

Ces fichiers et dossiers doivent **toujours** être inclus dans ta sauvegarde :

| Fichier / Dossier | Description |
| --- | --- |
| `_data/` | Items et paramètres d'inventaire |
| `_backups/` | Sauvegardes de la liste d'items |
| `_hooks/` | Recettes de craft et logique personnalisée |
| `_modules/` | Intégrations avec des scripts externes |
| `integrations/` | Paramètres d'intégration |
| `current_config.json` | Fichier de configuration principal |

#### Fichiers personnalisés

Ne sauvegarde ceux-ci que si tu les as modifiés ou ajoutés :

| Fichier / Dossier | Description |
| --- | --- |
| `_images/` | Images d'items personnalisées |
| `dist/assets/variables.css` | Couleurs de thème personnalisées |
| `_locales/` | Traductions personnalisées |
| `dist/menu_translations/` | Traductions de menu personnalisées |

<Note>
  Si tu n'as personnalisé aucun des fichiers listés ci-dessus, tu n'as pas besoin de les sauvegarder.
</Note>

### Processus de mise à jour

Suis ces étapes **dans l'ordre**.

### Référence rapide

| Fichier / Dossier | Sauvegarde requise | Utilité |
| --- | :-: | --- |
| `_data/` | Oui | Items et paramètres |
| `_backups/` | Oui | Sauvegardes de la liste d'items |
| `_hooks/` | Oui | Craft et logique personnalisée |
| `_modules/` | Oui | Intégrations externes |
| `integrations/` | Oui | Paramètres d'intégration |
| `current_config.json` | Oui | Configuration principale |
| `_images/` | Personnalisé | Images d'items personnalisées |
| `dist/assets/variables.css` | Personnalisé | Personnalisation du thème |
| `_locales/` | Personnalisé | Traductions personnalisées |
| `dist/menu_translations/` | Personnalisé | Traductions de menu |

### Dépannage

<AccordionGroup>
  <Accordion title="Mes items ont disparu">
    Restaure le dossier `_data/` depuis ta sauvegarde et redémarre le serveur.
  </Accordion>

  <Accordion title="Mes recettes de craft manquent">
    Restaure le dossier `_hooks/` depuis ta sauvegarde.
  </Accordion>

  <Accordion title="Mes paramètres ont été réinitialisés">
    Restaure `current_config.json` depuis ta sauvegarde.
  </Accordion>

  <Accordion title="Les couleurs de mon thème ont été réinitialisées">
    Restaure `dist/assets/variables.css` depuis ta sauvegarde si tu as personnalisé le thème par défaut.
  </Accordion>

  <Accordion title="Mes images personnalisées manquent">
    Restaure ton dossier `_images/` personnalisé.
  </Accordion>

  <Accordion title="Mes traductions manquent">
    Restaure `_locales/` et/ou `dist/menu_translations/`, selon les fichiers de traduction que tu as personnalisés.
  </Accordion>

  <Accordion title="Mon serveur ne démarre pas">
    1. Assure-toi que le nouveau dossier `jaksam_inventory` est correctement installé.
    2. Assure-toi que tes fichiers de sauvegarde ont été restaurés aux bons emplacements.
    3. Attends environ 30 secondes après le démarrage du serveur, car la base de données peut être en train de se mettre à jour automatiquement.
    4. Vérifie la console de ton serveur pour d'éventuelles erreurs.
    5. Si le problème persiste, restaure ta sauvegarde précédente et contacte le support.
  </Accordion>
</AccordionGroup>

### Important

<Warning>
  **Ne supprime jamais ta sauvegarde immédiatement après une mise à jour réussie.** Garde-la quelques jours au cas où tu découvrirais un problème plus tard.
</Warning>

<Check>
  Une fois que tout fonctionne correctement, ta mise à jour de Jaksam Inventory est terminée.
</Check>
