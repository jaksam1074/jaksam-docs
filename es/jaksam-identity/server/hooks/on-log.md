---
title: "On log"
description: "Envía cada línea del registro de admin de Jaksam Identity a Discord, a un servicio de logs o a tu panel de admin."
icon: "clipboard-list"
---

Cada línea que se escribe en el registro de admin (tabla `jksm_identity_log`) pasa también por aquí: expediciones, falsificaciones, documentos mostrados, cambios de estado, sucesos de los talleres, pasos de las redadas y cambios de config. Déjala vacía para no hacer nada.

Edita `Editable.OnLog` en `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.OnLog(action, fields)

end
```

```lua Example
local WEBHOOK = "https://discord.com/api/webhooks/..."

function Editable.OnLog(action, fields)
    if action ~= "issue" and action ~= "forge" and not action:find("^raid_") then return end
    local text = ("**%s** serial: %s actor: %s target: %s %s"):format(action,
        fields.serial or "-", fields.actor or "-", fields.target or "-", fields.detail or "")
    PerformHttpRequest(WEBHOOK, function() end, "POST",
        json.encode({ content = text }), { ["Content-Type"] = "application/json" })
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `action` | string | Qué ha pasado, por ejemplo `issue`, `forge`, `show`, `status`, `renew`, `ws_enter`, `ws_owner`, `raid_breach`, `raid_seize`, `npc_hire`, `config` |
| `fields` | table | `{ serial?, actor?, target?, detail? }`. `actor` y `target` son identificadores de personaje |
