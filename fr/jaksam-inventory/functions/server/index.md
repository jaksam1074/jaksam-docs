---
title: "Server"
icon: "server"
description: "Référence complète des exports côté serveur pour gérer les inventaires, items, planques et véhicules"
tag: "Updated"
---

## Compatibilité

Ce script fonctionne avec d'autres systèmes d'inventaire populaires, comme es_extended, qb-inventory et ox_inventory.

<Info>
  Pour les fonctions ESX et QBCore, la configuration se fait automatiquement. Mais si tu veux continuer à utiliser les exports d'ox_inventory ou qb-inventory pour la compatibilité, tu dois activer cette option dans le fichier : `jaksam_inventory/integrations/sv_integrations.lua`
</Info>

## Fonctions serveur

| Fonction | Description |
| --- | --- |
| [Add item](/fr/jaksam-inventory/functions/server/add-item) | Ajoute des items à un inventaire |
| [Add item to trunk](/fr/jaksam-inventory/functions/server/add-item-to-trunk) | Ajoute des items au coffre d'un véhicule via sa plaque |
| [Add item to glovebox](/fr/jaksam-inventory/functions/server/add-item-to-glovebox) | Ajoute des items à la boîte à gants d'un véhicule via sa plaque |
| [Remove item from trunk](/fr/jaksam-inventory/functions/server/remove-item-from-trunk) | Retire des items du coffre d'un véhicule via sa plaque |
| [Remove item from glovebox](/fr/jaksam-inventory/functions/server/remove-item-from-glovebox) | Retire des items de la boîte à gants d'un véhicule via sa plaque |
| [Get inventory ID from plate](/fr/jaksam-inventory/functions/server/get-inventory-id-from-plate) | Résout l'ID complet de l'inventaire pour un compartiment de véhicule |
| [Can carry item](/fr/jaksam-inventory/functions/server/can-carry-item) | Vérifie si un inventaire a de la place pour des items supplémentaires |
| [Can swap item](/fr/jaksam-inventory/functions/server/can-swap-item) | Vérifie si l'échange de deux items est possible |
| [Clear inventory](/fr/jaksam-inventory/functions/server/clear-inventory) | Retire tous les items d'un inventaire |
| [Create inventory](/fr/jaksam-inventory/functions/server/create-inventory) | Crée un nouvel inventaire en base de données et/ou en mémoire |
| [Force open inventory](/fr/jaksam-inventory/functions/server/force-open-inventory) | Force l'ouverture d'un inventaire pour un joueur spécifique |
| [Get inventory](/fr/jaksam-inventory/functions/server/get-inventory) | Récupère toutes les données d'un inventaire |
| [Get item from slot](/fr/jaksam-inventory/functions/server/get-item-from-slot) | Récupère un item depuis un slot spécifique |
| [Get item by name](/fr/jaksam-inventory/functions/server/get-item-by-name) | Récupère le premier item trouvé par son nom |
| [Get items by name](/fr/jaksam-inventory/functions/server/get-items-by-name) | Récupère tous les items trouvés par leur nom |
| [Get item label](/fr/jaksam-inventory/functions/server/get-item-label) | Récupère le label affiché d'un item |
| [Get total item amount](/fr/jaksam-inventory/functions/server/get-total-item-amount) | Retourne la quantité totale d'un item, y compris dans les containers |
| [Has item](/fr/jaksam-inventory/functions/server/has-item) | Vérifie si un inventaire a un item spécifique |
| [Register usable item](/fr/jaksam-inventory/functions/server/register-usable-item) | Enregistre un callback pour quand un item est utilisé |
| [Register stash](/fr/jaksam-inventory/functions/server/register-stash) | Enregistre dynamiquement une nouvelle planque |
| [Register item](/fr/jaksam-inventory/functions/server/register-item) | Enregistre une nouvelle définition d'item à l'exécution |
| [Register metadata template](/fr/jaksam-inventory/functions/server/register-metadata-template) | Ajoute un template de metadata depuis un script externe |
| [Remove item](/fr/jaksam-inventory/functions/server/remove-item) | Retire des items d'un inventaire |
| [Save dirty inventories](/fr/jaksam-inventory/functions/server/save-dirty-inventories) | Sauvegarde tous les inventaires modifiés dans la base de données |
| [Save dirty inventory](/fr/jaksam-inventory/functions/server/save-dirty-inventory) | Sauvegarde un inventaire spécifique dans la base de données |
| [Set inventory max weight](/fr/jaksam-inventory/functions/server/set-inventory-max-weight) | Définit la capacité de poids maximale d'un inventaire |
| [Set item metadata in slot](/fr/jaksam-inventory/functions/server/set-item-metadata-in-slot) | Met à jour les métadonnées d'un item dans un slot |
| [Set durability](/fr/jaksam-inventory/functions/server/set-durability) | Définit la valeur de durabilité d'un item dans un slot |
