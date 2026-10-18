---
title: "Bei Log"
description: "Jede Zeile des Admin-Protokolls von Jaksam Identity an Discord, einen Log-Dienst oder dein Admin-Panel senden."
icon: "clipboard-list"
---

Jede Zeile, die ins Admin-Protokoll (Tabelle `jksm_identity_log`) geschrieben wird, kommt auch hier vorbei: Ausstellungen, Fälschungen, Vorzeigen, Statusänderungen, Werkstatt-Ereignisse, Razzia-Schritte und Config-Änderungen. Lass sie leer für nichts.

Bearbeite `Editable.OnLog` in `editable/server.lua`:

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

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `action` | string | Was passiert ist, zum Beispiel `issue`, `forge`, `show`, `status`, `renew`, `ws_enter`, `ws_owner`, `raid_breach`, `raid_seize`, `npc_hire`, `config` |
| `fields` | table | `{ serial?, actor?, target?, detail? }`. `actor` und `target` sind Charakter-Identifier |
