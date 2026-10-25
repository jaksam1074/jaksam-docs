---
title: "Minijuegos"
description: "Elige los minijuegos de hackeo y de puente de Boosting Creator, usa scripts de minijuegos externos o añade el tuyo."
icon: "gamepad"
---

Dos minijuegos se eligen en **Ajustes > Robo** y **Ajustes > Rastreador**:

- **Minijuego del puente**: se juega en el asiento del conductor con **H**, cuando vehicles_keys no está en marcha. Su dificultad es el ajuste **Puente** de la clase.
- **Minijuego de hackeo**: se juega con **J** para hackear el rastreador GPS. Se vuelve más difícil con cada hackeo.

## Minijuegos disponibles

| Nombre | Qué es | Necesita |
| --- | --- | --- |
| `wires` | Arrastra cada cable de color al terminal del mismo color (puente por defecto) | |
| `signal` | Detén la aguja en movimiento sobre la señal, 3 aciertos, el auto se puede seguir conduciendo (hackeo por defecto) | |
| `skillcheck` | La barra de skill check | |
| `progressbar` | Una progress bar de 5 segundos, siempre sale bien (solo puente) | |
| `bruteforce` | Pantalla de hackeo por fuerza bruta | |
| `datacrack` | | `datacrack` |
| `fingerprint` | | `utk_fingerprint` |
| `memory_game` | | `ultra-keypackhack` |

Si un minijuego externo está en una carpeta con otro nombre, ponlo en `EXTERNAL_SCRIPTS_NAMES` en `integrations/cl_integrations.lua`.

<Info>
  El servidor verifica cada resultado. Los intentos sospechosos van al log **cheat** de Discord.
</Info>

## Crear tu propio minijuego

<Steps>
  <Step title="Copia el ejemplo">
    Copia `client/minigames/_EXAMPLE_MINIGAME.lua` en la misma carpeta, con un nombre nuevo, y quita las marcas de comentario del principio y del final.
  </Step>
  <Step title="Ponle nombre y llama a tu script">
    Fija `MINIGAME_NAME`. La función recibe la dificultad (de 1 a 3) y debe devolver `true` si sale bien y `false` si falla:

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
  <Step title="Fija el tiempo mínimo">
    Si tu minijuego siempre tarda unos segundos, añade su duración más corta en segundos a `minigamesMinSeconds` en `current_config.json`, junto a los valores que ya hay:

    ```json
    "my_minigame": 3
    ```
  </Step>
  <Step title="Elígelo">
    Reinicia el script. El nuevo minijuego aparece en la lista **Minijuego del puente** de los ajustes.

    La lista **Minijuego de hackeo** es fija: para hackear con tu propio minijuego, para el script, pon `"hackMinigame": "my_minigame"` en la parte `client` de `current_config.json` y vuelve a iniciarlo.
  </Step>
</Steps>
