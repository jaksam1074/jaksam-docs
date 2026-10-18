---
title: "Contrefaçon, ouvriers et commandes"
description: "Comment les joueurs fabriquent des faux à la main, comment la qualité est décidée, et comment fonctionnent les ouvriers PNJ et la file de commandes."
icon: "print"
---

## Fabriquer un faux à la main

Un faux passe par les postes de l'atelier, un ticket à la fois :

<Steps>
  <Step title="Photo">
    Devant le fond : prends-toi en photo ou un autre joueur, ou appelle un ouvrier PNJ avec un appareil photo. L'équipement pro donne un fond de photo transparent.
  </Step>
  <Step title="Saisie des données">
    Sur un ordinateur ou un portable : tape le nom, la date de naissance et les autres données imprimées.
  </Step>
  <Step title="Impression">
    Utilise une carte vierge et du toner de l'imprimante.
  </Step>
  <Step title="Plastification">
    À une table de plastification.
  </Step>
  <Step title="Gaufrage (optionnel)">
    Avec l'équipement pro uniquement, ajoute de la qualité.
  </Step>
  <Step title="Découpe">
    Au massicot : le document est terminé.
  </Step>
</Steps>

Chaque poste a un **skill check** : une réussite ajoute de la qualité, un échec en retire (`Config.Forging.check`, et `Config.Forging.emboss` pour la machine à gaufrer). Tu peux remplacer le mini-jeu, voir [Skill check](/fr/jaksam-identity/client/skill-check).

### Copies

Un joueur peut copier un document qu'il porte. Les données et la photo viennent de l'original, et les champs peuvent être modifiés : une vraie base avec un faux nom. La copie d'un faux est limitée à la qualité de l'original moins `Config.Forging.copyLoss`.

### Qualité

La qualité d'un faux (de 5 à 100) dépend de :

- le **niveau du faussaire** : chaque faux donne de l'expérience, et le niveau fixe la qualité de base et ce qui peut être falsifié (d'abord les identités, puis les licences, puis les cartes de service)
- les skill checks aux postes
- un peu de chance

Elle est ensuite limitée par l'**équipement** de l'atelier et la **carte vierge** utilisée (`doc_blank` jusqu'à 60, `doc_blank_secure` jusqu'à 100).

```lua
levels = {
    { xp = 0,    base = 35, kinds = { identity = true } },
    { xp = 150,  base = 45, kinds = { identity = true, license = true } },
    { xp = 500,  base = 58, kinds = { identity = true, license = true } },
    { xp = 1200, base = 70, kinds = { identity = true, license = true, badge = true } },
    { xp = 2500, base = 82, kinds = { identity = true, license = true, badge = true } },
},
```

La qualité décide quels défauts se voient au premier coup d'œil, en main, sous UV ou seulement au registre. Voir [Faux documents et anomalies](/fr/jaksam-identity/guides/documents-and-register#faux-documents-et-anomalies).

### Matériel

| Item | Utilisation |
| --- | --- |
| `doc_blank` | Carte vierge, qualité jusqu'à 60 |
| `doc_blank_secure` | Carte vierge sécurisée, qualité jusqu'à 100 |
| `printer_toner` | Cartouche de toner, `Config.Forging.tonerCharges` impressions chacune |
| `pvc_sheet` | Les ouvriers en font des cartes vierges |
| `holo_foil` | Les ouvriers en font, avec une carte vierge, une carte sécurisée |

Le matériel se commande sur un portable avec de l'argent sale et est livré au stockage des matières premières après un délai (`Config.Forging.orders`).

## Commandes

Une commande est un nombre de tickets d'un type de document et d'une carte vierge, dans lesquels piochent les ouvriers et les joueurs (d'abord les urgents, puis les plus anciens).

- **Priorité :** basse, normale ou urgente
- **Attribuée à :** tout le monde, un joueur ou un ouvrier
- **Mettre en pause, reprendre, annuler**
- **Données fixes :** une commande faite depuis une copie ou un jeu de données le répète sur ses tickets
- **Lots :** des identités inventées sans photo, confiées directement aux ouvriers
- **Confier :** un ticket peut être donné aux ouvriers, ou à un ouvrier, et repris

Chaque action demande un grade minimum dans le job :

```lua
queue = {
    maxAmount = 50,            -- tickets per order
    maxOpenTickets = 300,      -- open tickets per workshop
    offlineMinutes = 10,       -- an order assigned to a player who stays away this long goes back to everyone
    rights = { create = 0, priority = 1, assign = 2, pause = 1, cancel = 2, handover = 0 },
},
```

## Ouvriers PNJ

Le patron embauche des ouvriers sur le portable. Ils vont de machine en machine, passent les tickets par l'imprimante, la table de plastification et le massicot, rechargent les imprimantes en toner et portent les documents terminés au stockage des résultats.

| Niveau | Qualité de base | Vitesse | Taux d'échec | Tickets à la fois |
| --- | --- | --- | --- | --- |
| Débutant | 40 | 1.0 | 35% | 1 |
| Confirmé | 60 | 1.3 | 20% | 3 |
| Pro | 78 | 1.6 | 10% | 5 |

- **Rôles :** fabriquer des faux, ou produire du matériel (PVC en cartes vierges, carte et film en cartes sécurisées)
- **Cartes d'ouvrier :** sur un ouvrier tu vois le niveau, un statut en direct avec minuteur et des barres pour la vitesse, le taux d'échec, la taille de feuille et les cartouches. Donne des tâches directement : aller chercher du toner, prendre une commande ou un ticket, changer de rôle, renvoyer
- **Salaires :** le patron dépose de l'argent sale et les salaires sont prélevés une fois par période. Un ouvrier pas payé s'en va. Le temps sous scellés après une descente ne coûte rien
- **Garde :** un garde de sécurité par atelier prévient tout le monde à l'intérieur quand les agents commencent à enfoncer la porte
- La qualité d'un ouvrier ne dépasse jamais la qualité de base du meilleur faussaire joueur du job propriétaire
- Le nombre d'ouvriers dépend de l'amélioration d'équipement

Les prix d'embauche, salaires et temps de travail sont dans `config/npc.lua`, ou en jeu sur la page des ouvriers de `/documents config`.

<Tip>
  `Config.Bridge.menu = 'ox_lib'` remplace les cartes d'interaction des ouvriers et des postes par des menus contextuels ox_lib.
</Tip>

## Mode démo

Pour les vidéos de présentation et les serveurs de démo : les stockages sont toujours pleins, les temps de travail courts, rien ne coûte d'argent et personne n'échoue. Active-le avec `Config.Demo = true` ou `/documents demo on` (pas conservé après un redémarrage).
