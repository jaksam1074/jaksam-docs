---
title: "Can raid"
description: "Añade tus propias condiciones para reventar la puerta de un taller de falsificación."
icon: "building-shield"
---

Se llama cuando un agente empieza a reventar la puerta de un taller. Antes se comprueban el cuerpo y el rango, estar de servicio, que haya suficientes agentes conectados, el item del ariete y la espera desde la última redada. Devuelve `false` para bloquear el asalto.

Edita `Editable.CanRaid` en `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.CanRaid(src, workshopId)
    return true
end
```

```lua Example
-- Raids need a warrant from your MDT
function Editable.CanRaid(src, workshopId)
    return exports["my_mdt"]:HasWarrant("workshop", workshopId)
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `src` | integer | ID de servidor del agente |
| `workshopId` | string | El ID del taller, una clave de `Config.Forgery.workshops` |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `allowed` | boolean | **true** para permitir el asalto |
