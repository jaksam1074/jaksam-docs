---
title: "Classes et véhicules"
description: "Crée et règle les classes de Boosting Creator : réputation, paie, temps limite, police, traceur, gardes, poursuite par un gang, difficulté du démarrage aux fils, VIN scratch et casse."
icon: "ranking-star"
---

Une **classe** est un niveau de contrats. Cinq sont fournies avec le script, D, C, B, A et S, et tu peux les modifier ou ajouter les tiennes dans l'onglet **Classes** de `/boostingcreator`.

## Réglages d'une classe

| Champ | Ce qu'il fait |
| --- | --- |
| **ID** | Code court affiché sur la pastille de la classe. Il ne peut plus être changé après la création de la classe. |
| **Nom et couleur** | L'apparence de la classe dans le laptop, le HUD et le menu. |
| **Réputation pour la débloquer** | Un joueur ne reçoit des offres de cette classe qu'à partir de cette réputation. |
| **Réputation gagnée** | Donnée quand le contrat est terminé (livré, VIN effacé ou rangé). |
| **Paie minimum / maximum** | La paie de l'offre est aléatoire entre les deux. |
| **Temps limite** | Minutes pour finir le job, de 5 à 240. |
| **Policiers en service requis** | Les offres de cette classe n'arrivent qu'avec au moins ce nombre de policiers en ligne. |
| **Appel à la police à l'effraction** | Chance qu'un témoin appelle la police quand la voiture est forcée. |
| **Traceur GPS** | Activé ou non, et combien de piratages réussis le retirent (1 à 10). |
| **Gardes** | 1 à 6 gardes armés autour de la voiture garée, difficulté 1 à 5. |
| **Poursuite par un gang** | 1 à 3 voitures de poursuite, 1 à 3 tireurs en plus du conducteur, difficulté 1 à 5. |
| **Démarrage aux fils** | Facile, Moyen ou Difficile. Utilisé uniquement sans vehicles_keys. |
| **Peut être un contrat VIN scratch** | La classe peut sortir en contrat VIN scratch (quand le VIN scratch est activé dans les paramètres). |
| **Peut être un contrat de casse** | La classe peut sortir en contrat de casse (quand la casse est activée dans les paramètres). |

<Info>
  Supprimer une classe la retire aussi des fixers et des lieux qui l'utilisaient. Les voitures de cette classe déjà rangées dans un garage se vendent toujours.
</Info>

## Les classes par défaut

| Classe | Réputation | Risques |
| --- | --- | --- |
| D | 0 | aucun, casse autorisée |
| C | 60 | casse autorisée |
| B | 200 | traceur, casse autorisée |
| A | 500 | traceur, gardes, VIN scratch autorisé |
| S | 1000 | traceur, gardes, poursuite par un gang, VIN scratch autorisé |

## Véhicules

L'onglet **Véhicules** liste les voitures de chaque classe. Une classe peut avoir jusqu'à 60 véhicules, et chaque offre en choisit un au hasard.

- **Ajouter des véhicules** ouvre un sélecteur avec toutes les voitures vanilla et leur image.
- **Ajouter par nom de modèle** ajoute une voiture addon par son nom de spawn. Pour lui donner une image, mets un fichier `<nom de spawn>.webp` dans `boosting_creator/_vehicles_images/`, avec le nom écrit comme tu l'as ajouté, et redémarre le script.

<Tip>
  Une classe sans véhicule n'est jamais proposée. C'est pareil pour une classe sans zone de recherche ou livraison libre : voir [Lieux](/fr/boosting-creator/guides/locations).
</Tip>
