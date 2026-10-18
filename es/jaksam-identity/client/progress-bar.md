---
title: "Progress bar"
description: "Sustituye la progress bar que se usa al reventar una puerta, incautar pruebas y destruirlas."
icon: "spinner"
---

Todo lo que lleva tiempo y se puede abandonar (reventar una puerta, incautar, destruir pruebas) pasa por una sola función. Por defecto es `lib.progressBar` de ox_lib.

Edita `Editable.Progress` en `editable/client.lua`:

<CodeGroup>

```lua Function
function Editable.Progress(seconds, label)
    return lib.progressBar({
        duration = seconds * 1000, label = label, useWhileDead = false, canCancel = true,
        disable = { move = true, car = true, combat = true },
        anim = { dict = 'mini@repair', clip = 'fixing_a_player' },
    }) == true
end
```

```lua Example
function Editable.Progress(seconds, label)
    return exports['my_progressbar']:Start({
        time = seconds * 1000,
        text = label,
        cancelable = true,
    })
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `seconds` | number | Cuánto dura la acción |
| `label` | string | El texto que se muestra con la progress bar |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `completed` | boolean | **true** cuando llegó al final, **false** cuando el jugador la canceló |
