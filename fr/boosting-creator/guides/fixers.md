---
title: "Fixers"
description: "Les fixers de Boosting Creator : des acheteurs avec un nom qui envoient les contrats par e-mail, demandent une voiture sans une rayure, une repeinte ou du tuning, et paient plus à mesure qu'ils font confiance au voleur."
icon: "envelope"
---

Un **fixer** est un acheteur avec un nom. Au lieu d'une offre anonyme, le joueur reçoit un e-mail de sa part dans le laptop, et après le job une réponse dans la **Boîte de réception**. Les fixers sont activés par défaut et se règlent dans l'onglet **Fixers** de `/boostingcreator`.

## Réglages d'un fixer

| Champ | Ce qu'il fait |
| --- | --- |
| **Nom, initiales, couleur** | L'apparence du fixer dans les e-mails. |
| **Classes** | Les classes que le fixer achète. |
| **Réputation requise** | Le fixer n'écrit qu'aux joueurs qui ont cette réputation. |
| **Chance d'exigence** | À quelle fréquence le fixer demande quelque chose en plus. |
| **Exigences** | Jusqu'à 10, voir plus bas. |
| **Messages** | L'e-mail d'offre, et les réponses quand le job s'est bien passé, quand une exigence n'a pas été respectée et quand il a raté. |

Les messages peuvent utiliser `{model}`, `{class}`, `{pay}`, `{colour}`, `{mods}`, `{condition}` et `{amount}`.

## Exigences

Une exigence est une demande en plus sur un contrat de livraison :

| Type | La voiture doit |
| --- | --- |
| **Sans une rayure** | Arriver avec au moins un état donné, par exemple 95 %. |
| **Repeinte** | Arriver dans une des couleurs choisies. Elle apparaît dans une couleur très différente, donc elle doit être repeinte. |
| **Tuning par un mécano** | Avoir un certain nombre d'améliorations parmi moteur, freins et transmission niveau 2 ou plus, turbo et xénon. |

Chaque exigence a un **bonus** si elle est respectée, une **pénalité** si elle ne l'est pas, des **minutes en plus** sur le temps limite, la **confiance** dont elle a besoin, et le nombre de **mécanos** qui doivent être en ligne (jobs réglés dans **Paramètres > Contrats**). Pendant la conduite, la carte d'objectif indique à quelle distance la voiture est de l'exigence, et passe au vert quand elle est respectée.

## Confiance

Chaque personnage a un niveau de confiance de 0 à 100 avec chaque fixer. Plus de confiance augmente la paie, jusqu'à +20 % à confiance maximale par défaut, et débloque les exigences qui en ont besoin.

- Un job terminé (avec l'exigence respectée, ou sans exigence) ajoute de la confiance.
- Une exigence non respectée retire un peu de confiance.
- Un contrat raté ou expiré en retire plus.

Les montants se règlent dans **Paramètres > Contrats**.

## Les fixers par défaut

| Fixer | Achète | À partir de la réputation | Demande |
| --- | --- | --- | --- |
| Vinnie Russo | D à B | 0 | une voiture sans une rayure |
| Lola Navarro | C à S | 60 | une repeinte, avec un mécano en ligne |
| Dmitri Volkov | B à S | 200 | du tuning, et une voiture impeccable une fois qu'il te fait confiance |

<Info>
  Avec les fixers désactivés, ou quand aucun fixer n'achète la classe, l'offre est anonyme et n'a pas d'exigence.
</Info>
