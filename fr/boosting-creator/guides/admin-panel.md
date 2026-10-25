---
title: "Menu admin"
description: "Le menu admin de Boosting Creator : contrats en direct, joueurs en attente, profils des joueurs, paramètres et logs Discord."
icon: "sliders"
---

Ouvre le menu avec `/boostingcreator` ou `/boostcreator` (voir [Permission admin](/fr/boosting-creator/installation#permission-admin)). Chaque modification s'applique tout de suite, sans redémarrage.

| Onglet | À quoi il sert |
| --- | --- |
| **Classes** | Les [classes](/fr/boosting-creator/guides/classes-and-vehicles) et leurs risques |
| **Véhicules** | Les voitures de chaque classe |
| **Lieux** | [Tous les endroits](/fr/boosting-creator/guides/locations) du script |
| **Fixers** | Les [fixers](/fr/boosting-creator/guides/fixers) et leurs exigences |
| **En direct** | Les contrats en cours et les joueurs en attente |
| **Joueurs** | Profils, réputation, historique et garages |
| **Paramètres** | Tout le reste |

## En direct

Rafraîchi toutes les 5 secondes. Pour chaque contrat en cours : le joueur (et les membres de l'équipe), le fixer et l'exigence, la classe, le véhicule et la plaque, le trajet, l'état avec les badges traceur, poursuite et porte-voitures, et le temps restant. **Annuler** termine un contrat sans changement de réputation.

**Joueurs en attente** liste qui est en cooldown ou à la limite journalière, avec le temps restant et un bouton **Retirer le cooldown**.

<Frame>
  ![Onglet Live avec un contrat en cours](/images/boosting-creator/panel-live.jpg)
</Frame>

## Joueurs

Chaque profil de boosting, les joueurs en ligne en premier, avec une recherche par nom ou identifiant. Clique sur un profil pour l'ouvrir :

- réputation, niveau, contrats terminés et ratés, argent gagné
- **Définir la réputation** ou **Ajouter ou retirer de la réputation**
- le garage avec ses voitures, et un bouton pour retirer une voiture
- les 25 derniers contrats avec le fixer, l'exigence et la raison de la fin
- un menu danger : réinitialiser le profil, vider l'historique, reprendre le garage

## Paramètres

| Catégorie | Ce qu'il y a dedans |
| --- | --- |
| **Général** | Langue, permission ACE, item du laptop, compte qui reçoit la paie |
| **Contrats** | Rythme des offres, cooldowns et limite journalière, réputation et paie, VIN scratch, casse, équipes, fixers et confiance, garages, vente en gros et saisie, gardes, poursuite par un gang, appels à l'effraction |
| **Vol** | Mini-jeu des fils, attente avant un nouvel essai et alarme |
| **Traceur** | Pings, piratages et mini-jeu de piratage |
| **Modules** | Voir [Modules](/fr/boosting-creator/modules) |
| **Discord** | Logs et webhooks |

**Rétablir les valeurs par défaut** remet chaque paramètre comme il était à l'origine dans le script. Les classes, les lieux et les fixers ne sont pas touchés.

## Logs Discord

Avec les logs Discord activés, le script logue les fins de contrat (avec le fixer et l'exigence), les voitures arrivées trop vite pour être réelles, les traceurs coupés, les VIN scratch, les garages achetés, les porte-voitures mis en fourrière, les résultats de mini-jeux refusés et chaque modification admin. Tout va au webhook principal.

Pour envoyer un type de log ailleurs, ajoute-le à `specificWebhooks` dans `current_config.json`, avec les types `contracts`, `vin`, `garages`, `admin` et `cheat`.
