---
title: "Client"
description: "Exports côté client de Boosting Creator : remplace la notification d'aide, utilise le skill check depuis tes propres scripts."
icon: "laptop"
---

## Remplacer la notification d'aide

Les textes `Press E to ...` utilisent la notification d'aide native, ou le [module](/fr/boosting-creator/modules) **Text UI** que tu choisis dans les paramètres. Pour les afficher toi-même :

```lua
exports["boosting_creator"]:replaceShowHelpNotification(function(message)
    -- show message with your own UI
end)
```

La fonction est appelée à chaque frame tant que le texte doit être à l'écran.

## Skill check

La barre de skill check du script peut être utilisée par d'autres scripts.

```lua
local success = exports["boosting_creator"]:skillcheck(difficulty)
```

| Paramètre | Type | Description |
| --- | --- | --- |
| `difficulty` | `number` | 1 à 3 |
| `speed` | `number` (optionnel) | Vitesse du marqueur qui bouge, remplace la difficulté |
| `positiveBars` | `number` (optionnel) | Taille de la zone à atteindre, remplace la difficulté |

Retourne `true` en cas de réussite, `false` en cas d'échec ou quand un autre skill check est déjà ouvert. Il attend que le joueur ait fini.

Pour fermer un skill check ouvert (il retourne `false`) :

```lua
exports["boosting_creator"]:cancelSkillcheck()
```

## Notifications, barre de progression et dispatch

Ils se remplacent avec des [modules](/fr/boosting-creator/modules), pas avec des exports.

## Mini-jeux personnalisés

Voir [Ajouter ton propre mini-jeu](/fr/boosting-creator/guides/minigames#ajouter-ton-propre-mini-jeu).
