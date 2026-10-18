---
title: "On log"
description: "Send every line of the Jaksam Identity admin trail to Discord, a log service or your admin panel."
icon: "clipboard-list"
---

Every line written to the admin trail (table `jksm_identity_log`) passes here too: issues, forgeries, shows, status changes, workshop events, raid steps and config changes. Leave it empty for nothing.

Edit `Editable.OnLog` in `editable/server.lua`:

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `action` | string | What happened, for example `issue`, `forge`, `show`, `status`, `renew`, `ws_enter`, `ws_owner`, `raid_breach`, `raid_seize`, `npc_hire`, `config` |
| `fields` | table | `{ serial?, actor?, target?, detail? }`. `actor` and `target` are character identifiers |
