---
title: "Get rarities"
description: "Renvoie toutes les raretés configurées dans les paramètres de l'inventaire, avec leur label et leur couleur."
icon: "gem"
---

Renvoie toutes les raretés configurées dans les paramètres de l'inventaire, avec leur label et leur couleur. Pratique pour afficher les mêmes noms et couleurs de rareté dans tes propres shops, menus de craft ou HUD.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getRarities()
```

```lua Example
local rarities = exports['jaksam_inventory']:getRarities()

for rarityId, rarity in pairs(rarities) do
    print(rarityId, rarity.label, rarity.color) -- legendary  Legendary  #f0b105
end

-- Couleur de la rareté d'un item précis
local item = exports['jaksam_inventory']:getStaticItem('bread')
local color = item.rarity and rarities[item.rarity] and rarities[item.rarity].color
```

</CodeGroup>

### Paramètres

Aucun

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `rarities` | table | Raretés indexées par leur ID. Chacune est `{ label = string, color = string }`, où `color` est une couleur hexadécimale |

### Notes

- Les raretés sont celles définies dans le menu des paramètres `/inventory`, et l'export renvoie toujours les valeurs actuelles : tu peux donc l'appeler quand tu en as besoin au lieu de garder le résultat au démarrage
- L'ID de la rareté est la valeur que les items utilisent dans leur champ `rarity` (voir [Get static item](/fr/jaksam-inventory/functions/shared/get-static-item))
