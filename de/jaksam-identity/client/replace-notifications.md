---
title: "Benachrichtigungen"
description: "Die Standard-Benachrichtigungen von Jaksam Identity durch dein eigenes Benachrichtigungs-Script ersetzen."
icon: "bell"
---

`Config.Bridge.notify` in `config/main.lua` wählt eines der eingebauten Benachrichtigungssysteme:

| Wert | Benachrichtigungen |
| --- | --- |
| `esx` | `ESX.ShowNotification` |
| `qb` | `QBCore.Functions.Notify` |
| `qbox` | `exports.qbx_core:Notify` |
| `ox_lib` | `lib.notify` |
| `auto` | Nur QBCore-Version: wie das Framework |

## Eigene Benachrichtigungen nutzen

Bearbeite `Bridge.Notify` in `bridge/notify.lua`:

<CodeGroup>

```lua Function
function Bridge.Notify(message)

end
```

```lua Example
function Bridge.Notify(message)
    exports['my_notify']:Show({ title = 'Documents', text = message, duration = 5000 })
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `message` | string | Der Text, der dem lokalen Spieler angezeigt wird |
