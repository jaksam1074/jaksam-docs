---
title: "Register metadata template"
description: "Añade una plantilla de metadata desde un script externo, usada por los ítems con metadata dinámica."
icon: "tags"
---

Añade una plantilla de metadata desde un script externo. Una plantilla de metadata es una función que genera un valor de metadata cada vez que un ítem que la usa se añade a un inventario (un número de serie, el nombre del dueño, una estadística aleatoria, etc.).

Las plantillas registradas así funcionan exactamente como las de `metadata_templates.lua`: aparecen en el editor de ítems del menú de administración `/inventory`, donde puedes asignarlas a cualquier ítem. Consulta la [guía de Metadata](/es/jaksam-inventory/guides/metadata) para ver cómo se asignan las plantillas a los ítems.

<Note>
  Las plantillas solo se guardan en memoria. Se eliminan cuando tu script se detiene y se pierden cuando jaksam_inventory se reinicia, así que regístralas cada vez que tu script arranque.
</Note>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerMetadataTemplate(templateId, cb)
```

```lua Example
local function registerTemplates()
    exports['jaksam_inventory']:registerMetadataTemplate('my_serial', function(playerId, inventoryId, itemName, amount, metadata, slotId)
        return 'SN-' .. math.random(100000, 999999)
    end)
end

-- Registrar al arrancar, y otra vez si jaksam_inventory se reinicia después de tu script
registerTemplates()

AddEventHandler('onResourceStart', function(resourceName)
    if resourceName == 'jaksam_inventory' then registerTemplates() end
end)
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `templateId` | string | El ID de la plantilla, el que eliges en el editor de ítems |
| `cb` | function | Se llama cada vez que se añade un ítem que usa la plantilla. Lo que devuelve se convierte en el valor de la metadata |

#### Parámetros del callback

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `playerId` | number \| nil | ID de servidor del jugador, solo cuando el ítem se añade al inventario de un jugador |
| `inventoryId` | string | El inventario al que se añade el ítem |
| `itemName` | string | El ítem que se añade |
| `amount` | number | La cantidad que se añade |
| `metadata` | table \| nil | La metadata con la que se añade el ítem |
| `slotId` | string \| nil | El slot donde se añade el ítem, si se indicó uno |

### Valor de retorno

Ninguno

### Notas

- Solo del lado del servidor, porque la metadata siempre la genera el servidor
- Si el ID de tu plantilla coincide con uno de `metadata_templates.lua`, la tuya lo reemplaza mientras tu script está en marcha, y la original vuelve cuando tu script se detiene
- Mientras una plantilla no está registrada (tu script aún no ha arrancado o se ha detenido), los ítems que la usan se añaden con normalidad, solo que sin ese campo de metadata, y la consola del servidor muestra un aviso
