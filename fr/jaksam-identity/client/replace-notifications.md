---
title: "Notifications"
description: "Remplace les notifications par défaut de Jaksam Identity par ton propre script de notifications."
icon: "bell"
---

`Config.Bridge.notify` dans `config/main.lua` choisit l'un des systèmes de notifications intégrés :

| Valeur | Notifications |
| --- | --- |
| `esx` | `ESX.ShowNotification` |
| `qb` | `QBCore.Functions.Notify` |
| `qbox` | `exports.qbx_core:Notify` |
| `ox_lib` | `lib.notify` |
| `auto` | Version QBCore uniquement : comme le framework |

## Utiliser tes propres notifications

Modifie `Bridge.Notify` dans `bridge/notify.lua` :

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

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `message` | string | Le texte à afficher au joueur local |
