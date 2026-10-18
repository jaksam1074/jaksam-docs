---
title: "À chaque log"
description: "Envoie chaque ligne du journal admin de Jaksam Identity vers Discord, un service de logs ou ton panel admin."
icon: "clipboard-list"
---

Chaque ligne écrite dans le journal admin (table `jksm_identity_log`) passe aussi par ici : délivrances, faux, documents montrés, changements de statut, événements des ateliers, étapes des descentes et changements de config. Laisse-la vide pour ne rien faire.

Modifie `Editable.OnLog` dans `editable/server.lua` :

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

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `action` | string | Ce qui s'est passé, par exemple `issue`, `forge`, `show`, `status`, `renew`, `ws_enter`, `ws_owner`, `raid_breach`, `raid_seize`, `npc_hire`, `config` |
| `fields` | table | `{ serial?, actor?, target?, detail? }`. `actor` et `target` sont des identifiers de personnage |
