---
title: "Notifications"
description: "Replace the default notifications of Jaksam Identity with your own notification script."
icon: "bell"
---

`Config.Bridge.notify` in `config/main.lua` picks one of the built-in notification systems:

| Value | Notifications |
| --- | --- |
| `esx` | `ESX.ShowNotification` |
| `qb` | `QBCore.Functions.Notify` |
| `qbox` | `exports.qbx_core:Notify` |
| `ox_lib` | `lib.notify` |
| `auto` | QBCore version only: as the framework |

## Use your own notifications

Edit `Bridge.Notify` in `bridge/notify.lua`:

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `message` | string | The text to show to the local player |
