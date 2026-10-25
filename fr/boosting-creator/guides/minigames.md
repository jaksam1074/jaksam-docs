---
title: "Mini-jeux"
description: "Choisis les mini-jeux de piratage et de démarrage aux fils de Boosting Creator, utilise des scripts de mini-jeux externes, ou ajoute les tiens."
icon: "gamepad"
---

Deux mini-jeux se choisissent dans **Paramètres > Vol** et **Paramètres > Traceur** :

- **Mini-jeu des fils** : joué au siège conducteur avec **H**, quand vehicles_keys ne tourne pas. Sa difficulté est le réglage **Démarrage aux fils** de la classe.
- **Mini-jeu de piratage** : joué avec **J** pour pirater le traceur GPS. Il devient plus difficile au fil des piratages.

## Mini-jeux disponibles

| Nom | Ce que c'est | Nécessite |
| --- | --- | --- |
| `wires` | Glisse chaque fil de couleur sur la borne de la même couleur (démarrage aux fils par défaut) | |
| `signal` | Arrête l'aiguille qui bouge sur le signal, 3 réussites, la voiture peut toujours être conduite (piratage par défaut) | |
| `skillcheck` | La barre de skill check | |
| `progressbar` | Une barre de progression de 5 secondes, réussit toujours (démarrage aux fils uniquement) | |
| `bruteforce` | Écran de piratage en brute force | |
| `datacrack` | | `datacrack` |
| `fingerprint` | | `utk_fingerprint` |
| `memory_game` | | `ultra-keypackhack` |

Si un mini-jeu externe est dans un dossier avec un autre nom, règle-le dans `EXTERNAL_SCRIPTS_NAMES` dans `integrations/cl_integrations.lua`.

<Info>
  Chaque résultat est vérifié par le serveur. Les tentatives suspectes vont dans le log Discord **cheat**.
</Info>

## Ajouter ton propre mini-jeu

<Steps>
  <Step title="Copie l'exemple">
    Copie `client/minigames/_EXAMPLE_MINIGAME.lua` dans le même dossier, avec un nouveau nom, et retire les marques de commentaire au début et à la fin.
  </Step>
  <Step title="Nomme-le et appelle ton script">
    Règle `MINIGAME_NAME`. La fonction reçoit la difficulté (1 à 3) et doit retourner `true` en cas de réussite et `false` en cas d'échec :

    ```lua
    Minigames = Minigames or { registry = {} }
    local MINIGAME_NAME <const> = "my_minigame"

    Minigames.registry[MINIGAME_NAME] = function(difficulty)
        local promise = promise.new()

        TriggerEvent("my_minigame:start", difficulty, function(result)
            promise:resolve(result)
        end)

        return Citizen.Await(promise)
    end
    ```
  </Step>
  <Step title="Règle le temps minimum">
    Si ton mini-jeu dure toujours quelques secondes, ajoute sa durée la plus courte en secondes dans `minigamesMinSeconds` de `current_config.json`, à côté des valeurs déjà présentes :

    ```json
    "my_minigame": 3
    ```
  </Step>
  <Step title="Choisis-le">
    Redémarre le script. Le nouveau mini-jeu apparaît dans la liste **Mini-jeu des fils** des paramètres.

    La liste **Mini-jeu de piratage** est fixe : pour pirater avec ton propre mini-jeu, arrête le script, mets `"hackMinigame": "my_minigame"` dans la partie `client` de `current_config.json` et redémarre-le.
  </Step>
</Steps>
