---
title: "Hooks"
icon: "webhook"
description: "Intercepta y modifica el comportamiento del inventario con hooks del lado del servidor para transferencias, uso y creación de ítems"
tag: "Updated"
---

Los hooks son una forma de modificar el comportamiento del sistema de inventario. Se registran en el servidor y pueden usarse para modificar el comportamiento del sistema de inventario, por ejemplo para evitar que los jugadores muevan ítems a un inventario específico. Hay algunos ejemplos de hooks en la carpeta `jaksam_inventory/_hooks`.

## Buenas Prácticas

<CardGroup cols={3}>
  <Card title="Usa filtros" icon="filter">
    Usa siempre los filtros adecuados para evitar ejecuciones innecesarias de hooks
  </Card>

  <Card title="Retornos tempranos" icon="right-from-bracket">
    Usa retornos tempranos para salir de los hooks cuando no se cumplan las condiciones
  </Card>

  <Card title="Rendimiento" icon="gauge-high">
    Mantén la lógica de los hooks ligera para no afectar el rendimiento del inventario
  </Card>
</CardGroup>

## Ejemplos de Casos de Uso

- Evitar que los jugadores roben ítems que tienen el campo de metadato `sole_owner` (p. ej., ítems VIP)
- Evitar que los jugadores muevan armas policiales a su inventario personal
- Permitir solo una mochila por inventario de jugador
- Craftear ítems arrastrando un ítem específico sobre otro (por ejemplo, arrastrar pan sobre carne puede crear un sándwich)
- Bloquear el uso de ítems cuando el jugador está esposado o en zonas específicas
- Registrar estadísticas de uso de ítems y logros
- Evitar el uso de ciertos ítems dentro de vehículos
- Agregar ítems iniciales a los inventarios de jugadores nuevos cuando se crean
- Prepoblar contenedores de basura o stashes con ítems aleatorios al crearse

## Funciones de la API

### Registrar un Hook

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerHook(eventName, callback, options, priority)
```

</CodeGroup>

#### Parámetros

| Nombre | Tipo de Dato | Descripción |
| --- | --- | --- |
| `eventName` | string | El nombre del hook event a escuchar (consulta los [Events de Hook Disponibles](#events-de-hook-disponibles) más abajo) |
| `callback` | function | La función que se ejecuta cuando se activa el hook |
| `options` | table | Filtros y opciones de configuración (consulta el [Parámetro Options](#parametro-options) más abajo) |
| `priority` | number | Prioridad de ejecución (los números más altos se ejecutan primero, por defecto: 0) |

#### Valor de retorno

| Nombre | Tipo de Dato | Descripción |
| --- | --- | --- |
| `hookId` | string | Identificador único del hook registrado (se usa para anular el registro del hook) |

### Anular el Registro de un Hook

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterHook(hookId)
```

</CodeGroup>

#### Parámetros

| Nombre | Tipo de Dato | Descripción |
| --- | --- | --- |
| `hookId` | string | El identificador único devuelto al registrar el hook |

### Anular el Registro de Todos los Hooks de un Resource

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterResourceHooks(resourceName)
```

</CodeGroup>

#### Parámetros

| Nombre | Tipo de Dato | Descripción |
| --- | --- | --- |
| `resourceName` | string | Nombre del resource al que se le anulará el registro de todos los hooks |

## Parámetro Options

El parámetro options acepta una table con filtros para optimizar el rendimiento.

<Tabs>
  <Tab title="Común (todos los events)">
    ```lua
        local options = {
            -- Debug: Imprime en la consola cuando se activa el hook
            print = true,

            -- Solo activar para ítems específicos
            itemNameFilter = {
                bread = true,
                weapon_pistol = true
            },

            -- Solo activar para tipos de ítem específicos
            itemTypeFilter = {
                weapon = true,
                currency = true
            }
        }
    ```
  </Tab>
  <Tab title="Filtros de inventario">
    Para `onItemAdded`, `onItemRemoved`, `onInventoryCreated`, `onPreOpenInventory`, `onOmnipackTransaction`:

    ```lua
        local options = {
            -- Filtrar por tipo de inventario (recomendado)
            inventoryTypeFilter = {
                player = true,
                stash = true
            },

            -- Filtrar por patrones específicos de inventario (avanzado)
            inventoryFilter = {
                "player:.*",      -- Todos los jugadores
                "stash_police"    -- Stash específico
            }
        }
    ```
  </Tab>
  <Tab title="Filtros de transferencia">
    Solo para `onItemTransferred`:

    ```lua
        local options = {
            -- Filtrar el inventario de origen por tipo
            inventoryFromTypeFilter = { player = true },

            -- Filtrar el inventario de origen por patrón de nombre
            inventoryFromFilter = {
                "player:.*",      -- Todos los jugadores
                "vehicle:123"     -- Vehículo específico
            },

            -- Filtrar el inventario de destino por tipo
            inventoryToTypeFilter = { stash = true },

            -- Filtrar el inventario de destino por patrón de nombre
            inventoryToFilter = {
                "stash_police",   -- Stash específico
                "container:.*"    -- Todos los contenedores
            },

            -- Solo movimientos dentro del mismo inventario (arrastrar dentro del mismo inventario)
            intraInventoryOnly = true
        }
    ```
  </Tab>
</Tabs>

## Events de Hook Disponibles

| Event | Descripción |
| --- | --- |
| [Item added](/es/jaksam-inventory/hooks/on-item-added) | Se activa cuando se agrega un ítem a un inventario |
| [Item removed](/es/jaksam-inventory/hooks/on-item-removed) | Se activa cuando se elimina un ítem de un inventario |
| [Item transferred](/es/jaksam-inventory/hooks/on-item-transferred) | Se activa cuando un ítem se transfiere entre inventarios |
| [Omnipack transaction](/es/jaksam-inventory/hooks/on-omnipack-transaction) | Se activa cuando un admin crea o destruye un ítem a través del inventario de admin |
| [Pre use item](/es/jaksam-inventory/hooks/on-pre-use-item) | Se activa antes de que se use un ítem, puede cancelar el uso |
| [Post use item](/es/jaksam-inventory/hooks/on-post-use-item) | Se activa después de que se ha usado un ítem, solo como notificación |
| [Inventory created](/es/jaksam-inventory/hooks/on-inventory-created) | Se activa cuando se crea un nuevo inventario |
| [Pre open inventory](/es/jaksam-inventory/hooks/on-pre-open-inventory) | Se activa antes de que se abra un inventario secundario, puede impedir que se abra |

## Comportamiento de los Hooks

<CardGroup cols={2}>
  <Card title="Prioridad" icon="arrow-up-1-9">
    Los números más altos se ejecutan primero (por defecto: 0)
  </Card>

  <Card title="Valores de retorno" icon="reply">
    `return nil` o `return true`: permite que la acción continúe.

    `return false, "message", "notifyType"`: evita la acción y detiene la ejecución de los demás hooks. Los parámetros message y notifyType son opcionales (notifyType puede ser `"error"`, `"success"`, `"info"`)
  </Card>
</CardGroup>

<Note>
  **Excepción - [`onPreOpenInventory`](/es/jaksam-inventory/hooks/on-pre-open-inventory)**: el mensaje no se muestra al jugador, porque la precarga haría que se repitiese. Llama a `notifyPlayer` desde dentro del hook si quieres decirle al jugador el motivo.
</Note>

## Compatibilidad con ox_inventory

Cuando el resource de compatibilidad con ox_inventory está instalado, `exports.ox_inventory:registerHook(...)` se traduce a los hooks nativos de arriba, así que los scripts de ox_inventory funcionan sin cambios. Los payloads se transforman al formato de ox, y los nombres de opciones de ox (`itemFilter`, `typeFilter`, `inventoryFilter`, `print`) también se traducen.

| Hook de ox_inventory | Soportado | Hook nativo usado |
| --- | --- | --- |
| `createItem` | Sí | `onItemAdded` |
| `swapItems` | Sí | `onItemTransferred` |
| `openInventory` | Sí | `onPreOpenInventory` |
| `usingItem` | Sí | `onPreUseItem` |
| `buyItem` / `openShop` | No | todavía no hay hooks de tienda |
| `craftItem` | No | todavía no hay hooks de crafteo |

Registrar un hook no soportado imprime una advertencia y devuelve `nil` en lugar de lanzar un error.

Tres diferencias a tener en cuenta al migrar:

- Un hook de ox solo puede permitir o bloquear; no puede proporcionar un mensaje personalizado ni un tipo de notificación. Usa los hooks nativos para eso
- `openInventory` hereda el requisito de no tener estado descrito en [`onPreOpenInventory`](/es/jaksam-inventory/hooks/on-pre-open-inventory)
- **Los inventarios de jugador se identifican de forma distinta.** Los hooks de ox reciben el ID de servidor del jugador como number (`inventoryId = 4`), igual que ox_inventory. Los hooks nativos reciben el identificador de personaje de jaksam como string (`inventoryId = "char1:35030084..."`). Cualquier otro tipo de inventario usa el mismo ID string en ambos
