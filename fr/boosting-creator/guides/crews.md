---
title: "Équipes"
description: "Fais du boosting en équipe dans Boosting Creator : le chef invite les joueurs à proximité depuis le laptop, l'équipe partage chaque contrat, la paie est partagée avec un bonus."
icon: "users"
---

Les joueurs peuvent faire du boosting ensemble. Une **équipe**, c'est un chef et les joueurs qui ont accepté son invitation : elle rejoint la file comme un seul joueur et partage chaque contrat que le chef accepte.

## Créer une équipe

1. Le chef ouvre le laptop et va dans l'onglet **Équipe**. Les joueurs à moins de 10 m apparaissent dans la liste.
2. Le chef les invite. L'invitation dure 60 secondes.
3. Le joueur invité accepte depuis son propre laptop. À partir de là, le chef rejoint la file pour lui.

Le chef ne peut pas inviter pendant qu'un contrat est en cours. L'équipe prend fin quand le chef la dissout ou la quitte.

## Pendant un contrat

Chaque membre peut voler la voiture, la conduire, pirater le traceur, la livrer et la désosser dans une casse. La carte d'objectif et la carte du jeu sont les mêmes pour tout le monde.

Les offres suivent la réputation du chef.

Avec **Les grosses équipes affrontent plus** activé, une équipe plus grande affronte plus d'ennemis : un garde de plus pour chaque membre au-delà du premier (jusqu'à 6), et une voiture de poursuite de plus à partir de 3 membres (jusqu'à 3), sur les classes qui en ont.

## Paie et réputation

La paie augmente avec l'équipe et est partagée à parts égales :

```text
total = pay × (1 + bonus % × (members − 1))
share = total ÷ members
```

Avec le bonus par défaut de 50 %, un contrat de 10 000 fait par 2 joueurs paie 15 000 au total, 7 500 chacun. L'offre affiche la part de chaque membre.

Chaque membre reçoit la réputation de la classe, le contrat dans son historique et sa propre attente avant le prochain contrat.

## Paramètres

Dans **Paramètres > Contrats**, section **Équipe** :

| Paramètre | Par défaut |
| --- | --- |
| Équipes | activé. Désactivé, le laptop n'a pas d'onglet Équipe et tout le monde fait du boosting seul |
| Équipe la plus grande, chef compris | 4 joueurs (2 à 4) |
| Paie en plus par membre au-delà du premier | 50 % |
| Les grosses équipes affrontent plus | activé |

L'onglet **En direct** du menu liste les membres de chaque contrat en équipe.
