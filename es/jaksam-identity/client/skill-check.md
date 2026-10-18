---
title: "Skill check"
description: "Sustituye el minijuego de skill check de las estaciones de falsificación por el tuyo."
icon: "gamepad"
---

Cada estación de falsificación hace un skill check: un acierto añade calidad a la falsificación, un fallo la quita. Por defecto es `lib.skillCheck` de ox_lib.

Edita `Editable.SkillCheck` en `editable/client.lua`:

<CodeGroup>

```lua Function
function Editable.SkillCheck(difficulty)
    return lib.skillCheck(difficulty, { 'e' })
end
```

```lua Example
function Editable.SkillCheck(difficulty)
    -- one round of your own minigame per difficulty step
    for _ = 1, #difficulty do
        if not exports['my_minigame']:Start() then return false end
    end
    return true
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `difficulty` | table | La dificultad de `config/forgery.lua`: `Config.Forging.check.difficulty` (por defecto `{ 'easy', 'medium' }`), o `Config.Forging.emboss.difficulty` en la máquina de relieve |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `success` | boolean | **true** si el jugador ha superado el check |

Cuánta calidad añade un acierto y quita un fallo se fija en `Config.Forging.check` y `Config.Forging.emboss` (`success`, `failure`).
