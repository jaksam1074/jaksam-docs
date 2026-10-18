---
title: "On raid"
description: "Envía un aviso de dispatch o tu propia alarma cuando avanza una redada en un taller de falsificación."
icon: "tower-broadcast"
---

Se llama cada vez que una redada avanza. Es el sitio para tu aviso de dispatch o tu propia alarma.

Edita `Editable.OnRaid` en `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.OnRaid(workshopId, phase, src)

end
```

```lua Example
function Editable.OnRaid(workshopId, phase, src)
    if phase == "breach" then
        local workshop = Config.Forgery.workshops[workshopId]
        exports["my_dispatch"]:Alert({
            job = "police",
            title = "Raid in progress",
            message = ("Officers are breaching %s"):format(workshop and workshop.label or workshopId),
            coords = src and GetEntityCoords(GetPlayerPed(src)),
        })
    end
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `workshopId` | string | El ID del taller, una clave de `Config.Forgery.workshops` (los talleres añadidos en el juego también están ahí) |
| `phase` | string | `breach` (un agente empezó a reventar la puerta), `aborted` (se abandonó el asalto), `open` (la puerta cedió, los agentes pueden entrar), `over` (la redada terminó, el taller está precintado) |
| `src` | integer \| nil | ID de servidor del agente que lo hizo, **nil** cuando se acabó el tiempo o lo hizo un admin |
