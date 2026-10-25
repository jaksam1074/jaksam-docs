---
title: "Police"
description: "Ce que la police voit et fait dans Boosting Creator : appels à l'effraction, pings du traceur GPS, modules de dispatch, minimum de policiers par classe et saisies de porte-voitures."
icon: "shield-halved"
---

## Jobs de police

Les jobs qui comptent comme police sont listés dans `integrations/sh_integrations.lua` :

```lua
POLICE_JOBS_NAMES = {
    ["police"] = true,
    ["sheriff"] = true,
}
```

Les joueurs avec ces jobs :

- reçoivent les pings du traceur et les appels à l'effraction
- comptent pour les **policiers en service requis** de chaque classe et du porte-voitures
- ne peuvent pas rejoindre la file de boosting
- peuvent saisir un porte-voitures et l'amener à une fourrière

## Appels à l'effraction

Quand une voiture de contrat est forcée, le réglage **Appel à la police à l'effraction** de la classe décide si un témoin appelle la police. L'appel arrive après 10 secondes (par défaut, **Paramètres > Contrats > Appel à la police à l'effraction > Avance avant l'appel**) via le [module de dispatch](/fr/boosting-creator/modules). Il est tiré une seule fois par contrat, et fonctionne aussi sur les classes sans traceur.

## Traceur GPS

Sur les classes avec un traceur, une fois la voiture volée, chaque policier voit un cercle rouge avec un blip **Traceur \<plaque\>** toutes les 6 secondes, avec un bip. Le premier ping indique aussi le modèle et la plaque.

Les voleurs piratent le traceur avec **J** (modifiable dans les touches de FiveM sous "Boosting : pirater le traceur"). Les passagers peuvent toujours pirater, le conducteur seulement à l'arrêt. Chaque piratage réussi agrandit le cercle, chaque piratage raté envoie un ping tout de suite. Quand le dernier piratage réussit, les policiers voient **Signal du traceur perdu**.

| Paramètre (**Paramètres > Traceur**) | Par défaut |
| --- | --- |
| Secondes entre deux pings à la police | 6 |
| Secondes entre deux piratages | 8 |
| Agrandissement du cercle de ping par piratage | 60 m |
| Le conducteur peut pirater quand le véhicule est à l'arrêt | activé |

Avec un module de dispatch autre que `default`, ton dispatch reçoit aussi un appel quand le suivi commence.

## Porte-voitures

Voir [Garages et porte-voitures](/fr/boosting-creator/guides/garages-and-car-carrier#police) : un cercle qui suit le porte-voitures, la saisie en prenant le volant, et la récompense à la fourrière.
