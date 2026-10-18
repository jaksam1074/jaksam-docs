---
title: "Can enter workshop"
description: "Añade tus propias condiciones para entrar en un taller de falsificación."
icon: "door-open"
---

Se llama cuando un jugador entra en un taller de falsificación. Antes se comprueba que el jugador es miembro del trabajo propietario, desde el `minGrade` del taller. Devuelve `false` para dejarlo fuera.

Edita `Editable.CanEnterWorkshop` en `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.CanEnterWorkshop(src, workshopId)
    return true
end
```

```lua Example
-- Nobody enters while wanted by the police
function Editable.CanEnterWorkshop(src, workshopId)
    return not exports["my_wanted"]:IsWanted(src)
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `src` | integer | ID de servidor del jugador |
| `workshopId` | string | El ID del taller, una clave de `Config.Forgery.workshops` |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `allowed` | boolean | **true** para dejar entrar al jugador |
