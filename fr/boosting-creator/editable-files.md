---
title: "Fichiers modifiables"
description: "Les fichiers de Boosting Creator faits pour être modifiés : format des plaques, jobs de police, debug, noms des events externes, garage QBCore et les hooks."
icon: "file-pen"
---

La plupart de Boosting Creator se configure en jeu. Quelques réglages se trouvent plutôt dans le dossier `integrations/`, parce que ce sont du code ou parce qu'ils changent rarement.

<Warning>
  Garde une copie de ces fichiers avant de mettre le script à jour : une mise à jour peut les remplacer.
</Warning>

## integrations/sh_integrations.lua

| Valeur | Ce qu'elle fait |
| --- | --- |
| `EXAMPLE_PLATE` | Format des plaques des contrats. Les lettres et les chiffres sont aléatoires, `#` marque la partie fixe : `"#BST#123"` donne `BST920`, `BST945`... 8 caractères maximum. |
| `POLICE_JOBS_NAMES` | Les jobs qui comptent comme [police](/fr/boosting-creator/guides/police). |
| `SECONDS_TO_REFRESH_SHARED_OBJECT` | Rafraîchit l'objet du framework toutes les X secondes, `nil` pour ne jamais le rafraîchir. |
| `DEBUG_OUTPUTS` | Lignes de debug dans la console du serveur et dans F8. Aussi possible avec `setr boosting_creator_debug 1` dans `server.cfg`, sans modifier le fichier. Active-le quand tu demandes du support. |

## integrations/sv_integrations.lua

| Valeur | Ce qu'elle fait |
| --- | --- |
| `EXTERNAL_EVENTS_NAMES` | À changer uniquement si ton framework a renommé ses events et que le script ne les trouve pas. |
| `VIN_SCRATCH_QB_GARAGE` | QBCore uniquement : le garage où une voiture au VIN effacé est enregistrée, `pillboxgarage` par défaut. |
| `CanPlayerJoinBoostingQueue` | [Hook](/fr/boosting-creator/server#canplayerjoinboostingqueue) pour empêcher un joueur de rejoindre la file. |
| `OnBoostingContractEnded` | [Hook](/fr/boosting-creator/server#onboostingcontractended) appelé quand un contrat se termine. |

## integrations/cl_integrations.lua

| Valeur | Ce qu'elle fait |
| --- | --- |
| `DEFAULT_PROGRESSBAR_COLOR` | Couleur de la barre de progression par défaut, un code hexadécimal. |
| `BLIP_TIME_AFTER_POLICE_ALERT` | Secondes pendant lesquelles le blip d'alerte du module de dispatch `default` reste sur la carte, 120 par défaut. |
| `EXTERNAL_SCRIPTS_NAMES` | Noms des dossiers de `datacrack`, `utk_fingerprint` et `ultra-keypackhack`, si tu les as renommés. |

## current_config.json

Les réglages du menu sont enregistrés dans `boosting_creator/current_config.json`. Modifie-les depuis le menu. Deux valeurs n'y ont pas de champ :

- `specificWebhooks` : un webhook Discord par type de log, voir [Logs Discord](/fr/boosting-creator/guides/admin-panel#logs-discord)
- `minigamesMinSeconds` : le temps le plus court qu'un mini-jeu peut prendre, voir [Mini-jeux](/fr/boosting-creator/guides/minigames#ajouter-ton-propre-mini-jeu)

Arrête le script avant de modifier le fichier à la main, sinon le menu peut enregistrer par-dessus ta modification.
