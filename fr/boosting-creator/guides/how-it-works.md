---
title: "Fonctionnement d'un contrat"
description: "Le côté joueur de Boosting Creator : le laptop, la file, les offres, le vol de la voiture, le traceur et les façons dont un contrat peut se terminer."
icon: "route"
---

Cette page suit un contrat du laptop jusqu'à la paie, comme le joueur le voit.

## Le laptop et la file

Le joueur utilise l'item **laptop de boosting** et appuie sur **Rejoindre la file**. La file reste active après la fermeture du laptop : une petite pastille à l'écran indique depuis combien de temps il attend.

- Les jobs de police ne peuvent pas rejoindre la file (voir [Police](/fr/boosting-creator/guides/police)).
- Après un contrat, il peut y avoir une attente avant la prochaine offre, et une limite journalière par personnage. Les deux se règlent dans **Paramètres > Contrats** et s'affichent sur la même pastille sous forme de compte à rebours.

## L'offre

Toutes les 45 à 120 secondes (par défaut), un joueur dans la file reçoit une offre pour une classe qu'il a débloquée, avec assez de policiers en ligne et un emplacement libre pour faire apparaître la voiture. Les classes plus hautes sortent plus souvent une fois débloquées.

L'offre affiche la classe, le véhicule, la paie ou "le véhicule est à toi", la réputation qu'elle donne, le temps limite et les risques : traceur, gardes, poursuite par un gang, difficulté du démarrage aux fils. Elle est anonyme, ou c'est un e-mail d'un [fixer](/fr/boosting-creator/guides/fixers) qui peut demander quelque chose en plus. Le joueur accepte ou refuse dans les 60 secondes.

Si le laptop est fermé, l'offre arrive sous forme de notification avec un son de téléphone.

<Frame>
  ![Laptop de boosting avec une offre de contrat](/images/boosting-creator/laptop-offer.jpg)
</Frame>

## Trouver la voiture

Un cercle jaune apparaît sur la carte. La voiture est quelque part à l'intérieur, jamais au centre, et le cercle se resserre autour d'elle à mesure que le joueur s'approche. La voiture n'est créée que quand quelqu'un est à proximité, verrouillée, avec sa propre plaque. Des gardes armés peuvent se tenir autour.

<Frame>
  ![Carte d'objectif d'un contrat en cours](/images/boosting-creator/objective-card.jpg)
</Frame>

## La voler

<Tabs>
  <Tab title="Sans vehicles_keys">
    1. **Effraction** : à pied à côté de la voiture, appuie sur **E** et réussis le skill check. Chaque tentative déclenche l'alarme et alerte les gardes.
    2. **Démarrage aux fils** : au siège conducteur, appuie sur **H** et joue au mini-jeu du démarrage aux fils (relier les fils de couleur par défaut). Facile, Moyen ou Difficile selon la classe. Une erreur fait des étincelles, une courte attente, et déclenche l'alarme.
  </Tab>
  <Tab title="Avec vehicles_keys">
    Le joueur crochète la serrure ou casse la vitre et démarre aux fils avec vehicles_keys, comme pour n'importe quelle autre voiture. La voiture volée reçoit des clés temporaires, retirées à la fin du contrat.
  </Tab>
</Tabs>

Une effraction peut être **repérée** : selon la classe, un témoin appelle la police quelques secondes plus tard. La carte d'objectif l'indique alors.

## Prendre la fuite

Une fois la voiture volée :

- **Traceur GPS** (classes qui en ont un) : la police voit un cercle autour de la voiture toutes les quelques secondes. Les passagers, ou le conducteur à l'arrêt, le piratent avec **J**, plusieurs fois de suite. Quand le dernier piratage réussit, le signal est perdu.
- **Poursuite par un gang** (classes qui en ont une) : des voitures avec des tireurs apparaissent derrière le voleur. Elle se termine quand elles sont détruites, semées, ou après quelques minutes.

La livraison n'est affichée qu'une fois le traceur disparu.

## Terminer le contrat

| Fin | Ce qui se passe |
| --- | --- |
| **Livraison** | Arrête-toi dans le marqueur vert et appuie sur **E**. Un acheteur marche jusqu'à la voiture, monte et part avec. La paie baisse avec les dégâts de la voiture. |
| **VIN scratch** | Dans une carrosserie, à pied, appuie sur **E** : après 10 secondes la voiture est au joueur, enregistrée dans son garage. Pas d'argent. |
| **Casse** | Démonte les portières, le capot, le coffre et les roues un par un et porte chaque pièce au point de dépôt. Chaque pièce paie sa part tout de suite. |
| **Son propre garage** | Sur un contrat de livraison simple, la voiture peut plutôt être rangée dans le [garage](/fr/boosting-creator/guides/garages-and-car-carrier) du joueur, pour la vendre plus tard. |

Un contrat **échoue** quand le temps est écoulé, que le joueur meurt, que la voiture est détruite ou disparue, ou que le joueur l'abandonne depuis le laptop. Un contrat raté ou expiré fait perdre un peu de réputation.

## Réputation

Chaque classe donne de la réputation quand le job est terminé. La réputation débloque les classes suivantes et fait monter le niveau affiché dans le laptop. Le laptop garde aussi l'historique des derniers contrats et le total gagné.
