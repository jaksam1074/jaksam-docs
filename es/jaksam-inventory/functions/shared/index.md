---
title: "Shared"
icon: "circle-share-nodes"
description: "Exports que funcionan tanto en el servidor como en el cliente"
tag: "Updated"
---

## Compatibilidad

Este script funciona con otros sistemas de inventario populares, como es_extended, qb-inventory y ox_inventory.

<Info>
  Para las funciones de ESX y QBCore, la configuración se realiza automáticamente. Pero si quieres seguir usando exports de ox_inventory o qb-inventory por compatibilidad, debes activar esta opción en el archivo: `jaksam_inventory/integrations/sv_integrations.lua`
</Info>

## Funciones Shared

| Función | Descripción |
| --- | --- |
| [Get static items list](/es/jaksam-inventory/functions/shared/get-static-items-list) | Devuelve la lista de todos los ítems del inventario |
| [Get static item](/es/jaksam-inventory/functions/shared/get-static-item) | Obtiene información genérica del ítem (peso, si es apilable, descripción, etc.) |
| [Get item label](/es/jaksam-inventory/functions/shared/get-item-label) | Obtiene solo el label (nombre para mostrar) de un ítem |
| [Get item image path](/es/jaksam-inventory/functions/shared/get-item-image-path) | Obtiene la ruta de imagen NUI de un ítem |
| [Get rarities](/es/jaksam-inventory/functions/shared/get-rarities) | Devuelve todas las rarezas configuradas en los ajustes, con label y color |
