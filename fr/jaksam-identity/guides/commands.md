---
title: "Commandes"
description: "Liste complète des commandes admin /documents et des commandes joueur de Jaksam Identity."
icon: "slash-forward"
---

## Qui peut les utiliser

`/documents <sous-commande>` fonctionne depuis la console du serveur, pour les joueurs avec l'ACE `jksm_identity.admin`, et pour les groupes du framework de `Config.AdminGroups`. Sans sous-commande, il les liste toutes.

```cfg
add_ace group.admin jksm_identity.admin allow
```

Le nom de la commande est `Config.AdminCommand` (par défaut `documents`).

## Commandes admin

| Sous-commande | Ce qu'elle fait |
| --- | --- |
| `config` | Ouvre les [réglages en jeu](/fr/jaksam-identity/guides/settings-in-game) |
| `issue <playerId> <type> [nophoto] [force] [grant] [grant:<licence type>]` | Délivre un vrai document |
| `check <serial>` | Contrôle au registre comme le voit une autorité |
| `truth <serial>` | Vue admin : authentique, faux (avec qualité et auteur) ou inconnu |
| `license <playerId> list \| add <type> \| remove <type>` | Licences d'un personnage |
| `forge <playerId> <type> <quality 0-100> [nophoto] [copy:<serial>]` | Donne un faux |
| `workshop <job> \| leave` | Entre dans un atelier ou en sort |
| `exit <playerId> \| all` | Fait sortir des joueurs des ateliers |
| `toner <job> <prints>` | Règle le toner de l'imprimante d'un atelier |
| `raid [<workshop> [end \| unseal \| reset]]` | Liste les descentes et les scellés, termine une descente, lève des scellés, efface l'attente avant la prochaine descente |
| `order <job> <type> <amount> [low\|normal\|urgent] [assignee]` | Crée une commande |
| `orders <job>` | Liste les commandes d'un atelier |
| `ordercmd <job> <id> <action> [value]` | Gère une commande |
| `demo on \| off \| refill` | Mode démo pour les présentations (`Config.Demo`) |

### Options de issue

| Option | Effet |
| --- | --- |
| `nophoto` | Délivre sans prendre de photo |
| `force` | Délivre même si la licence ou le job manque |
| `grant` | Donne aussi au personnage toutes les licences du document |
| `grant:<licence type>` | Donne aussi au personnage une licence, par exemple `grant:drive_truck` |

```bash
/documents issue 12 id_card            # ID card with photo for player 12
/documents issue 12 drive grant        # driver licence, granting the licence first
/documents check SAAB1234567           # what the police would see
/documents forge 12 drive 80           # a forged driver licence of quality 80
```

<Note>
  Avec `Config.Debug = true`, il y a aussi des commandes de mesure (`/jksm_pos`, `/jksm_aim`, ...) et des sous-commandes de test, pour les admins uniquement. Désactive `Config.Debug` sur un serveur en production : elles n'existent alors plus.
</Note>

## Commandes joueur

| Commande | Ce qu'elle fait |
| --- | --- |
| `/businesscards` | Imprime des cartes de visite pour ton job, voir [Cartes de visite](/fr/jaksam-identity/guides/business-cards) |
