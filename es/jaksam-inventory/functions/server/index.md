---
title: "Server"
icon: "server"
description: "Referencia completa de los exports del lado del servidor para gestionar inventarios, ítems, stashes y vehículos"
tag: "Updated"
---

## Compatibilidad

Este script funciona con otros sistemas de inventario populares, como es_extended, qb-inventory y ox_inventory.

<Info>
  Para las funciones de ESX y QBCore, la configuración se realiza automáticamente. Pero, si quieres seguir usando los exports de ox_inventory o qb-inventory por compatibilidad, debes activar esta opción en el archivo: `jaksam_inventory/integrations/sv_integrations.lua`
</Info>

## Funciones de servidor

| Función | Descripción |
| --- | --- |
| [Add item](/es/jaksam-inventory/functions/server/add-item) | Añade ítems a un inventario |
| [Add item to trunk](/es/jaksam-inventory/functions/server/add-item-to-trunk) | Añade ítems a un maletero de vehículo por matrícula |
| [Add item to glovebox](/es/jaksam-inventory/functions/server/add-item-to-glovebox) | Añade ítems a una guantera de vehículo por matrícula |
| [Remove item from trunk](/es/jaksam-inventory/functions/server/remove-item-from-trunk) | Elimina ítems de un maletero de vehículo por matrícula |
| [Remove item from glovebox](/es/jaksam-inventory/functions/server/remove-item-from-glovebox) | Elimina ítems de una guantera de vehículo por matrícula |
| [Get inventory ID from plate](/es/jaksam-inventory/functions/server/get-inventory-id-from-plate) | Resuelve el ID completo del inventario de un compartimento del vehículo |
| [Can carry item](/es/jaksam-inventory/functions/server/can-carry-item) | Comprueba si un inventario tiene espacio para ítems adicionales |
| [Can swap item](/es/jaksam-inventory/functions/server/can-swap-item) | Comprueba si es posible intercambiar dos ítems |
| [Clear inventory](/es/jaksam-inventory/functions/server/clear-inventory) | Elimina todos los ítems de un inventario |
| [Create inventory](/es/jaksam-inventory/functions/server/create-inventory) | Crea un nuevo inventario en la base de datos y/o en memoria |
| [Force open inventory](/es/jaksam-inventory/functions/server/force-open-inventory) | Fuerza la apertura de un inventario para un jugador específico |
| [Get inventory](/es/jaksam-inventory/functions/server/get-inventory) | Obtiene los datos completos de un inventario |
| [Get item from slot](/es/jaksam-inventory/functions/server/get-item-from-slot) | Obtiene un ítem de un slot específico |
| [Get item by name](/es/jaksam-inventory/functions/server/get-item-by-name) | Obtiene el primer ítem encontrado por nombre |
| [Get items by name](/es/jaksam-inventory/functions/server/get-items-by-name) | Obtiene todos los ítems encontrados por nombre |
| [Get item label](/es/jaksam-inventory/functions/server/get-item-label) | Obtiene la etiqueta visible de un ítem |
| [Get total item amount](/es/jaksam-inventory/functions/server/get-total-item-amount) | Devuelve la cantidad total de un ítem, incluyendo contenedores |
| [Has item](/es/jaksam-inventory/functions/server/has-item) | Comprueba si un inventario tiene un ítem específico |
| [Register usable item](/es/jaksam-inventory/functions/server/register-usable-item) | Registra un callback para cuando se usa un ítem |
| [Register stash](/es/jaksam-inventory/functions/server/register-stash) | Registra dinámicamente un nuevo stash |
| [Register item](/es/jaksam-inventory/functions/server/register-item) | Registra una nueva definición de ítem en tiempo de ejecución |
| [Register metadata template](/es/jaksam-inventory/functions/server/register-metadata-template) | Añade una plantilla de metadata desde un script externo |
| [Remove item](/es/jaksam-inventory/functions/server/remove-item) | Elimina ítems de un inventario |
| [Save dirty inventories](/es/jaksam-inventory/functions/server/save-dirty-inventories) | Guarda todos los inventarios modificados en la base de datos |
| [Save dirty inventory](/es/jaksam-inventory/functions/server/save-dirty-inventory) | Guarda un inventario específico en la base de datos |
| [Set inventory max weight](/es/jaksam-inventory/functions/server/set-inventory-max-weight) | Establece la capacidad máxima de peso de un inventario |
| [Set item metadata in slot](/es/jaksam-inventory/functions/server/set-item-metadata-in-slot) | Actualiza la metadata de un ítem en un slot |
| [Set durability](/es/jaksam-inventory/functions/server/set-durability) | Establece el valor de durabilidad de un ítem en un slot |
