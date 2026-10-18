---
title: "Notifications"
description: "Sustituye las notificaciones por defecto de Jaksam Identity por tu propio script de notificaciones."
icon: "bell"
---

`Config.Bridge.notify` en `config/main.lua` elige uno de los sistemas de notificaciones incluidos:

| Valor | Notificaciones |
| --- | --- |
| `esx` | `ESX.ShowNotification` |
| `qb` | `QBCore.Functions.Notify` |
| `qbox` | `exports.qbx_core:Notify` |
| `ox_lib` | `lib.notify` |
| `auto` | Solo versión QBCore: como el framework |

## Usa tus propias notificaciones

Edita `Bridge.Notify` en `bridge/notify.lua`:

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

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `message` | string | El texto que se muestra al jugador local |
