---
title: "Garages et porte-voitures"
description: "Les garages de Boosting Creator : achètes-en un, range les voitures volées dans 6 places, sors-les pour une vente, ou vends tout le garage sur un porte-voitures que la police peut saisir."
icon: "warehouse"
---

Les voleurs peuvent acheter un **garage** et garder les voitures volées au lieu de les vendre tout de suite. Plus tard, ils les sortent une par une, ou les chargent toutes sur un **porte-voitures** pour une plus grosse paie. Les deux sont activés par défaut, dans **Paramètres > Contrats**, sections **Garages** et **Vente en gros**.

## Acheter un garage

Les garages sont des [lieux](/fr/boosting-creator/guides/locations#garages) avec un prix. L'onglet **Garage** du laptop liste ceux qui sont à vendre avec un bouton de waypoint.

À l'entrée, à pied, un panneau affiche le nom, le quartier, le prix et les 6 places. Appuie deux fois sur **E** en moins de 3 secondes pour l'acheter. L'argent vient du compte réglé dans **Compte qui paie les garages**.

Chaque personnage possède un seul garage. Plusieurs joueurs peuvent acheter le même garage : chacun entre dans sa propre copie privée de l'intérieur, avec ses propres 6 voitures.

<Frame>
  ![Panneau de l'entrée du garage avec le prix](/images/boosting-creator/garage-entrance.jpg)
</Frame>

## Ranger une voiture

Sur un contrat de livraison simple (sans exigence d'un fixer, ni VIN scratch ni casse), une fois la voiture volée, l'objectif indique **ou range-la dans ton garage**. Arrête-toi dans le rayon de l'entrée et appuie sur **E**.

La voiture est rangée avec sa valeur : la paie du contrat multipliée par l'état de la voiture. Le joueur reçoit la réputation de la classe, mais pas encore d'argent. Un garage plein (6 voitures) n'est pas proposé.

## Dans le garage

Appuie sur **E** à l'entrée pour entrer. Les voitures rangées sont à leur place, et le panneau liste chacune avec sa classe et sa valeur.

Pour en **sortir** une, appuie sur **E** à côté d'elle. La voiture apparaît à la **sortie des voitures** du garage avec le voleur au volant, et une livraison vers un acheteur libre commence tout de suite : déjà volée, sans traceur, sans gardes, sans poursuite, qui paie la valeur rangée multipliée par l'état à la livraison. La place est libérée quelle que soit l'issue.

## Tout vendre sur le porte-voitures

Avec au moins **3 voitures** (par défaut), le panneau intérieur affiche deux totaux : une par une, et sur le porte-voitures avec un multiplicateur, de x1.3 avec les voitures requises jusqu'à x2 avec un garage plein. Appuie deux fois sur **G** en moins de 3 secondes pour démarrer.

- Un camion avec sa remorque apparaît au **départ du porte-voitures** du garage, attelé et avec les voitures dessus, le voleur au volant.
- L'acheteur est un **acheteur en gros** à au moins 2 500 m du garage.
- Il faut **2 policiers en service** (par défaut) et il y a une limite de 30 minutes.
- La remorque doit rester attelée : si elle est laissée à plus de 150 m derrière pendant une minute, la vente échoue.

### Police

Après 20 secondes, la police reçoit un cercle autour du porte-voitures, déplacé toutes les 40 secondes. Si le camion reste immobile, le cercle se resserre à chaque mise à jour.

Un policier qui prend le volant **saisit** le porte-voitures : la vente échoue et le policier reçoit un itinéraire vers la **fourrière** la plus proche. S'y arrêter paie au compte société une récompense fixe plus une part de la valeur du chargement, et un bonus optionnel au policier.

### Plan B

À l'arrêt, à pied au bout de la rampe, le voleur appuie sur **E** : la dernière voiture descend et devient sa propre livraison à sa valeur rangée. Le reste du chargement est perdu.
