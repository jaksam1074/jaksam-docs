---
title: "Shared"
icon: "circle-share-nodes"
description: "Exports qui fonctionnent à la fois côté serveur et côté client"
tag: "Updated"
---

## Compatibilité

Ce script fonctionne avec d'autres systèmes d'inventaire populaires, comme es_extended, qb-inventory et ox_inventory.

<Info>
  Pour les fonctions ESX et QBCore, la configuration se fait automatiquement. Mais si tu veux continuer à utiliser les exports d'ox_inventory ou qb-inventory pour la compatibilité, tu dois activer cette option dans le fichier : `jaksam_inventory/integrations/sv_integrations.lua`
</Info>

## Fonctions partagées

| Fonction | Description |
| --- | --- |
| [Get static items list](/fr/jaksam-inventory/functions/shared/get-static-items-list) | Retourne la liste de tous les items de l'inventaire |
| [Get static item](/fr/jaksam-inventory/functions/shared/get-static-item) | Récupère les informations génériques d'un item (poids, empilable, description, etc.) |
| [Get item label](/fr/jaksam-inventory/functions/shared/get-item-label) | Récupère uniquement le label (nom affiché) d'un item |
| [Get item image path](/fr/jaksam-inventory/functions/shared/get-item-image-path) | Récupère le chemin d'image NUI d'un item |
| [Get rarities](/fr/jaksam-inventory/functions/shared/get-rarities) | Renvoie toutes les raretés configurées dans les paramètres, avec label et couleur |
