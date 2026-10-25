---
title: "Lieux"
description: "Tous les types de lieux de Boosting Creator : zones de recherche, livraisons, carrosseries VIN, casses, garages avec leur sortie des voitures et leur départ du porte-voitures, acheteurs en gros et fourrières."
icon: "location-dot"
---

Tous les endroits du script se règlent dans l'onglet **Lieux** de `/boostingcreator`. Chacun a un nom, une position avec orientation et un rayon. **Ma position** les remplit à partir de l'endroit où tu te tiens, ou du véhicule dans lequel tu es assis, au niveau du sol.

Depuis le menu de la ligne, tu peux t'y **téléporter**, placer un **waypoint**, ou afficher un **aperçu** d'une zone de recherche (une voiture transparente apparaît à l'emplacement pendant 15 secondes).

## Types de lieux

| Type | Ce que c'est | Rayon |
| --- | --- | --- |
| **Zone de recherche** | L'endroit où la voiture du contrat est garée. La position est la place de parking exacte, le rayon est le cercle que le joueur fouille. | 30 à 500 m |
| **Livraison** | L'acheteur. La voiture doit s'arrêter dans le rayon. | 2 à 20 m |
| **Carrosserie VIN** | L'endroit où un contrat VIN scratch emmène la voiture. | 2 à 20 m |
| **Casse** | L'endroit où un contrat de casse emmène la voiture. Elle a un deuxième point, le **point de dépôt des pièces**, où le voleur porte chaque pièce. | 2 à 20 m |
| **Garage** | Un garage que les voleurs peuvent acheter. Voir [plus bas](#garages). | 2 à 20 m |
| **Acheteur en gros** | Prend un [porte-voitures](/fr/boosting-creator/guides/garages-and-car-carrier#tout-vendre-sur-le-porte-voitures) entier. Il faut un terrain dégagé pour un camion avec sa remorque. | 2 à 20 m |
| **Fourrière** | L'endroit où les policiers amènent un porte-voitures saisi. | 2 à 20 m |

Les zones de recherche, les livraisons, les carrosseries VIN et les casses peuvent être limitées à certaines **classes**. Aucune sélectionnée veut dire toutes les classes.

<Tip>
  Place une zone de recherche avec une vraie voiture : assieds-toi dedans, garée entre les lignes et tournée dans le sens voulu, et appuie sur **Ma position**. La voiture du contrat apparaît exactement là.
</Tip>

## Un contrat par emplacement

Une offre réserve sa zone de recherche et sa livraison jusqu'à la fin du contrat, donc deux joueurs n'ont jamais la même voiture ou le même acheteur en même temps. Avec beaucoup de joueurs qui font du boosting en même temps, ajoute plus de lieux : une classe sans zone de recherche ou livraison libre n'est tout simplement pas proposée.

## Garages

Un garage a trois points :

| Point | Où le placer |
| --- | --- |
| **Entrée** | À pied devant la porte du garage. Les joueurs achètent le garage et y entrent ici, et arrêtent une voiture dans son rayon pour la ranger. |
| **Sortie des voitures** | L'endroit où apparaît une voiture sortie du garage, avec le voleur au volant. Assieds-toi dans une voiture garée là et appuie sur **Ma position**. |
| **Départ du porte-voitures** | L'endroit où apparaît le camion quand tout le garage est vendu. La remorque apparaît 11 m droit derrière, donc laisse de la place. Assieds-toi dans un véhicule à cet endroit, tourné vers la route, et appuie sur **Ma position**. |

Un garage a aussi un **prix**. Il n'utilise pas les classes : n'importe quel voleur peut l'acheter.

<Warning>
  Un garage déjà acheté par des joueurs ne peut pas être supprimé. Reprends-le-leur d'abord, dans l'onglet **Joueurs**.
</Warning>

<Frame>
  ![Lieu de garage avec entrée, sortie de la voiture et départ du porte-voitures](/images/boosting-creator/panel-garage.jpg)
</Frame>

## Les lieux par défaut

Le script est fourni avec 10 zones de recherche, 5 livraisons, 1 casse, 1 carrosserie VIN, 6 garages (Vespucci Beach, LSIA, Elysian Island, Sandy Shores, Grapeseed, Paleto Bay), 4 acheteurs en gros et 1 fourrière. Ils sont ajoutés une seule fois : si tu les supprimes, ils ne reviennent pas.
