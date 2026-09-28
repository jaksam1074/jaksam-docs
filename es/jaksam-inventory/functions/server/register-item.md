---
title: "Register item"
description: "Registra una nueva definición de ítem en tiempo de ejecución (solo en memoria, no se guarda en archivo)."
icon: "cube"
---

Registra una nueva definición de ítem en tiempo de ejecución (solo en memoria, no se guarda en archivo). Solo se aceptan campos seguros y declarativos, cualquier otra cosa se rechaza a cualquier profundidad.

<Note>
  Los ítems registrados de esta forma se perderán al reiniciar el resource. Úsalo para permitir que scripts externos definan sus propios ítems sin editar `_data/items.lua`.
</Note>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerItem(itemName, itemData)
```

```lua Example: consumable
-- Registra un ítem consumible simple
local success, err = exports['jaksam_inventory']:registerItem('energy_drink', {
    label = 'Energy Drink',
    weight = 0.3,
    stackable = true,
    maxStack = 10,
    description = 'Restores some energy',
    image = 'energy_drink.webp',
    consume = 1,
    status = { hunger = 5, thirst = 15 },
})

if not success then
    print('Failed to register item: ' .. err)
end
```

```lua Example: weapon
-- Registra un ítem de tipo arma
local success, err = exports['jaksam_inventory']:registerItem('WEAPON_YOURWEAPON', {
    label = 'Custom Weapon',
    weight = 2.0,
    stackable = false,
    type = 'weapon',
    ammo = 'ammo_9mm',
    durability = 0.15,
    decay = true,
})
```

```lua Example: container
-- Registra un ítem de tipo contenedor
local success, err = exports['jaksam_inventory']:registerItem('custom_bag', {
    label = 'Custom Bag',
    weight = 1.0,
    stackable = false,
    type = 'container',
    inventoryOptions = {
        maxSlots = 5,
        maxWeight = 10.0,
    },
})
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `itemName` | string | Identificador único del ítem (por ejemplo, `'custom_radio'`). No debe existir ya en el registro de ítems |
| `itemData` | table | Tabla de definición del ítem (ver Notas más abajo para los campos aceptados) |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `success` | boolean | True si el ítem se registró correctamente |
| `errorMessage` | string \| nil | Descripción del error si el registro falló |

### Notas

`itemData` solo acepta los siguientes campos seguros; cualquier otro campo se elimina silenciosamente:

**Campos obligatorios:** `label` (string), `weight` (number, >= 0), `stackable` (boolean)

**Campos opcionales:** `description`, `image`, `close`, `maxStack`, `rarity`, `type`, `customSymbol`, `ammo`, `durability`, `degrade`, `decay`, `consume`, `isGrenadeType`, `separateWeight`, `universal`, `oxClientEvent`, `oxClientExport`, `oxServerExport`

**Campos de tipo table opcionales** (validados recursivamente, no se permiten funciones dentro): `metadata`, `status`, `useOptions`, `inventoryOptions`, `throwableOptions`, `dynamicMetadata`

Además:

- Los ítems registrados con `registerItem` existen solo en memoria. Se pierden al reiniciar el resource. Si necesitas ítems persistentes, usa el menú de administración en el juego o añádelos a `_data/items.lua`
- Los ítems desconocidos para el inventario nunca se eliminan: se ocultan en el inventario donde están y vuelven automáticamente en cuanto el ítem se registra de nuevo, así que tu script puede llamar a `registerItem` en cualquier momento, normalmente al iniciar el resource
- Puedes combinar `registerItem` con `registerUsableItem` para definir tanto el ítem como su comportamiento de uso desde un script externo
- Si el nombre del ítem ya existe, el registro se rechaza para evitar sobrescribir ítems definidos por archivo
- Los campos de tipo table (como `metadata`, `useOptions`, etc.) se copian en profundidad, por lo que los cambios en la tabla original después del registro no tienen efecto
