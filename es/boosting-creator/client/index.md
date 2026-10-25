---
title: "Client"
description: "Exports del lado del cliente de Boosting Creator: sustituye la notificación de ayuda y usa el skill check desde tus propios scripts."
icon: "laptop"
---

## Sustituir la notificación de ayuda

Los textos `Press E to ...` usan la notificación de ayuda nativa, o el [módulo](/es/boosting-creator/modules) de **Text UI** que elijas en los ajustes. Para dibujarlos tú mismo:

```lua
exports["boosting_creator"]:replaceShowHelpNotification(function(message)
    -- show message with your own UI
end)
```

La función se llama en cada frame mientras el texto debe estar en pantalla.

## Skill check

Otros scripts pueden usar la barra de skill check del script.

```lua
local success = exports["boosting_creator"]:skillcheck(difficulty)
```

| Parámetro | Tipo | Descripción |
| --- | --- | --- |
| `difficulty` | `number` | De 1 a 3 |
| `speed` | `number` (opcional) | Velocidad del marcador en movimiento, sustituye a la dificultad |
| `positiveBars` | `number` (opcional) | Tamaño de la zona que hay que acertar, sustituye a la dificultad |

Devuelve `true` si sale bien, `false` si falla o si ya hay otro skill check abierto. Espera hasta que el jugador termina.

Para cerrar un skill check abierto (devuelve `false`):

```lua
exports["boosting_creator"]:cancelSkillcheck()
```

## Notificaciones, progress bar y dispatch

Se sustituyen con [módulos](/es/boosting-creator/modules), no con exports.

## Minijuegos personalizados

Mira [Crear tu propio minijuego](/es/boosting-creator/guides/minigames#crear-tu-propio-minijuego).
