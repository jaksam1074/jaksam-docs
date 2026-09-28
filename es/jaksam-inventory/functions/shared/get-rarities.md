---
title: "Get rarities"
description: "Devuelve todas las rarezas configuradas en los ajustes del inventario, con su label y su color."
icon: "gem"
---

Devuelve todas las rarezas configuradas en los ajustes del inventario, con su label y su color. Útil para mostrar los mismos nombres y colores de rareza en tus propias tiendas, menús de crafteo o HUDs.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getRarities()
```

```lua Example
local rarities = exports['jaksam_inventory']:getRarities()

for rarityId, rarity in pairs(rarities) do
    print(rarityId, rarity.label, rarity.color) -- legendary  Legendary  #f0b105
end

-- Color de la rareza de un ítem concreto
local item = exports['jaksam_inventory']:getStaticItem('bread')
local color = item.rarity and rarities[item.rarity] and rarities[item.rarity].color
```

</CodeGroup>

### Parámetros

Ninguno

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `rarities` | table | Rarezas indexadas por su ID. Cada una es `{ label = string, color = string }`, donde `color` es un color hexadecimal |

### Notas

- Las rarezas son las definidas en el menú de ajustes `/inventory`, y el export siempre devuelve las actuales, así que puedes llamarlo cuando las necesites en lugar de guardar el resultado al inicio
- El ID de la rareza es el valor que los ítems usan en su campo `rarity` (ver [Get static item](/es/jaksam-inventory/functions/shared/get-static-item))
