---
title: "Numéro de téléphone"
description: "Imprime le numéro de téléphone d'un autre script de téléphone sur les cartes de visite."
icon: "phone"
---

Le numéro de téléphone imprimé sur les cartes de visite vient de `Bridge.Phone.Number`. `Config.Bridge.phone` choisit RoadPhone (`'roadphone'`) ou rien (`'none'`).

Pour utiliser un autre script de téléphone, modifie `bridge/phone.lua` :

<CodeGroup>

```lua Function
function Bridge.Phone.Number(src)

end
```

```lua Example
function Bridge.Phone.Number(src)
    local ok, number = pcall(function() return exports["my_phone"]:GetNumber(src) end)
    return ok and number and tostring(number) or ""
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `src` | integer | ID serveur du joueur |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `number` | string | Le numéro de téléphone, ou `""` s'il est inconnu |
