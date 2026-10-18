---
title: "Réglages en jeu"
description: "Change les frais, les mairies, les ateliers, les prix, les salaires et les règles des descentes en jeu avec /documents config, sans redémarrer."
icon: "sliders"
---

Les admins changent la plupart des réglages en jeu avec `/documents config` : pas de fichier à modifier, pas de redémarrage.

## Ce qu'il contient

| Section | Réglages |
| --- | --- |
| **Général** | Utiliser et montrer les documents, numéros de documents, langue |
| **Mairies** | Documents de départ, frais, les mairies elles-mêmes |
| **Ateliers** | Les ateliers avec prix et propriétaire, règles d'achat et de vente, prix des améliorations, commandes de matériel, stockages, règles de contrefaçon et de commandes |
| **Ouvriers** | Frais d'embauche, salaires, temps de travail, mode démo |
| **Descentes** | Règles, unités avec leurs salles des scellés, la porte, la saisie |

## Comment ça marche

- **Les changements sont regroupés et appliqués ensemble.** Ce que tu changes est marqué, et une barre en bas enregistre tout (**Apply**) ou l'annule (**Discard**). Rien n'atteint les joueurs avant.
- **Les lieux se placent avec la caméra.** **Place** te laisse te déplacer et viser : un fantôme du PNJ se tient là où tu regardes, la molette le fait tourner, un clic prend l'emplacement. **Here** prend l'endroit où tu te trouves, et tu peux te téléporter à un lieu enregistré.
- **Les jobs se choisissent dans la liste du framework.** Les durées s'affichent en secondes, minutes, heures ou jours, les chances en pourcentage.
- **En vigueur tout de suite** pour tout le serveur après **Apply**. Une exception marquée attend le prochain démarrage du script : la taille des stockages.
- **La langue** change tout de suite pour tout le monde : menus, targets, blips et libellés de la config.

## Fichiers et base de données

Les fichiers de config restent les valeurs par défaut. Une valeur modifiée est gardée en base (table `jksm_identity_settings`) et prime sur le fichier. Chaque valeur peut revenir à sa valeur par défaut en un clic, et chaque changement est écrit dans le log avec l'admin qui l'a fait.

<Note>
  Ceux-ci restent dans `config/main.lua`, car ils sont nécessaires pendant le chargement du script : framework, inventaire et target, les droits admin, `Config.Debug` et les noms des items.
</Note>
