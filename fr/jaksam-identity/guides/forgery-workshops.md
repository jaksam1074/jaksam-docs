---
title: "Ateliers de faussaires"
description: "Ajoute des ateliers de faussaires, laisse les jobs les acheter et les vendre, et configure les améliorations, les stockages et qui peut entrer."
icon: "warehouse"
---

Un atelier est une porte quelque part dans le monde qui mène à sa propre copie de la salle des faussaires (l'intérieur des faux papiers des bikers de `bob74_ipl`). Il appartient à un job ou à personne.

<Warning>
  **Aucun atelier n'est configuré de base.** Tout le côté contrefaçon reste invisible tant que tu n'en ajoutes pas un dans `config/forgery.lua` ou en jeu avec `/documents config`.
</Warning>

## Ajouter un atelier

Dans `Config.Forgery.workshops` (`config/forgery.lua`) :

```lua
workshops = {
    docks = { label = 'Docks', entrance = vec4(0.0, 0.0, 0.0, 0.0), price = 150000, jobs = {}, minGrade = 0 },
    east_side = { label = 'East side', entrance = vec4(0.0, 0.0, 0.0, 0.0), price = 90000, jobs = { 'vagos', 'ballas' }, minGrade = 1 },
},
```

| Champ | Description |
| --- | --- |
| `label` | Nom de l'atelier |
| `entrance` | La porte à l'extérieur, un `vec4` avec l'orientation pour sortir |
| `price` | Ce qu'un job paie pour l'acheter |
| `jobs` | Les jobs qui peuvent le posséder, `{}` pour tous |
| `minGrade` | Grade le plus bas du job propriétaire qui peut entrer |
| `owner` | Optionnel : le job auquel il appartient dès le premier démarrage |

<Tip>
  C'est plus simple en jeu : sur la page des ateliers de `/documents config`, appuie sur **Place**, va jusqu'à la porte et clique. Les admins y ajoutent et retirent aussi des ateliers pendant que le serveur tourne, et donnent un atelier à un job ou le lui reprennent.
</Tip>

## Acheter et posséder

- **Acheter :** un atelier sans propriétaire affiche "Workshop for sale" à sa porte. Le patron d'un job l'achète pour le job avec de l'argent sale (`Config.Forgery.payAccount`).
- **Plusieurs par job :** un job peut en posséder autant qu'il peut payer, ou autant que `ownership.perJob` le permet.
- **Qui est le patron :** le grade le plus haut du job propriétaire, et autant de grades en dessous que `ownership.bossDepth` l'indique. Le patron achète, vend, embauche et améliore.
- **Les membres** du job propriétaire entrent à partir du `minGrade` de l'atelier. Les autres sonnent, et un membre à l'intérieur peut les faire entrer.
- **Vendre :** le patron le vend sur le portable de l'atelier (page Upgrades) et récupère `ownership.refund` de ce qui a été payé (rien pour un atelier donné par un admin). `ownership.sellable = false` désactive la vente.

```lua
ownership = {
    perJob = 0,           -- workshops one job may own (0 = as many as it can pay)
    bossDepth = 0,        -- ranks below a job's highest that may buy, sell and manage too
    sellable = true,      -- the boss may sell the workshop at its laptop
    refund = 0.5,         -- share of what was paid that comes back when it is sold
    onRelease = 'room',   -- what stays when a workshop loses its owner
},
```

### Ce qui reste quand un atelier perd son propriétaire

| `onRelease` | Résultat |
| --- | --- |
| `room` | Les améliorations et les stockages restent, les ouvriers sont renvoyés et les commandes en cours abandonnées |
| `all` | Tout reste pour le prochain propriétaire |
| `nothing` | Une salle vide |

<Info>
  **Argent sale :** sur ESX le compte `black_money`, sur QBCore l'item `markedbills` (sa valeur dans `metadata.worth`), sur Qbox l'item empilable `black_money`.
</Info>

## Améliorations

Le patron achète les améliorations sur le portable, avec de l'argent sale.

| Amélioration | Ce qu'elle change |
| --- | --- |
| **Équipement** | La qualité maximale qu'un faux fait ici peut atteindre (aucun, basique jusqu'à 70, pro jusqu'à 100), combien d'ouvriers tiennent, et la machine à gaufrer (pro uniquement) |
| **Sécurité** | Le temps qu'il faut aux agents pour enfoncer la porte (30 secondes, 90 avec l'amélioration), et une alarme aux membres ailleurs pendant une descente |
| **Style** | L'apparence de l'intérieur |

Les prix sont dans `Config.Forgery.upgrades`, ou en jeu.

## Le portable du patron

Le portable du bureau du patron affiche sa page sur le vrai écran de la salle, avec des onglets :

- **Vue d'ensemble :** ouvriers, machines et tables
- **Personnel :** embaucher et renvoyer les ouvriers et le garde, payer les salaires, choisir ce que les ouvriers détruisent pendant une descente
- **Tickets :** la file des commandes
- **Matériel :** commander du matériel, livré au stockage des matières premières après un délai
- **Upgrades :** acheter des améliorations, vendre l'atelier

## Stockages

Chaque atelier a trois stockages qui s'ouvrent à leurs étagères :

| Stockage | Contenu |
| --- | --- |
| Matières premières | Cartes vierges, toner et tout ce dont la contrefaçon a besoin |
| Libre | Libre pour les joueurs |
| Résultats | Là où les ouvriers déposent les documents terminés |

Les tailles sont dans `Config.Forging.stores`. Les ouvriers mettent les documents d'une commande dans une **pile d'ID** (`id_stack`), un conteneur qui les garde dans un seul slot. Glisser un document sur un autre fait aussi une pile. qb-inventory n'a pas de conteneurs, les documents y arrivent un par un.

<Note>
  Chaque target porte à 2 mètres (`Config.TargetDistance`), et le serveur n'accepte les actions que d'un membre qui se tient au poste. Les invités et les agents à l'intérieur ne voient aucun poste.
</Note>
