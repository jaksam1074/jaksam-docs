---
title: "Pre open inventory"
description: "Hook activado antes de que un inventario secundario se envíe al cliente, puede impedir que se abra."
icon: "door-open"
---

Se activa ANTES de que un inventario secundario (stash, maletero, guantera, tienda, drop, contenedor, el inventario de otro jugador, ...) se envíe al cliente. Este hook puede impedir que el inventario se abra. Regístralo con [`registerHook`](/es/jaksam-inventory/hooks#registrar-un-hook) usando el nombre de event `onPreOpenInventory`.

Abrir tu **propio** inventario de jugador nunca activa este hook.

### Payload

| Campo | Tipo de Dato | Descripción |
| --- | --- | --- |
| `playerId` | number | El jugador que abre el inventario |
| `inventoryId` | string | p. ej. `"stash_07ABC"` |
| `inventoryType` | string | `player`, `stash`, `shop`, `trunk`, `glovebox`, `container`, `ground_container`, `dumpster`, `omnipack` |
| `slotId` | number \| nil | Solo para contenedores: el slot del ítem contenedor en el inventario padre |

<Note>
  Este hook puede impedir que el inventario se abra devolviendo `false`. Los datos nunca salen del servidor, así que es un control de acceso real (restricción por trabajo/banda/whitelist), no solo una comprobación de UI.
</Note>

**Filtros disponibles:** `inventoryTypeFilter` e `inventoryFilter`.

### Prefiere hooks sin estado

Cuando un jugador pulsa la tecla del inventario, el cliente precarga los inventarios cercanos (stashes a menos de 3m de una posición configurada, además de maleteros, guanteras, tiendas, contenedores de basura y drops cercanos) antes de que se abra la UI, y cada precarga activa este hook. Por tanto tu callback puede ejecutarse varias veces para el mismo inventario, e incluso para inventarios que el jugador nunca llega a abrir.

Esto solo afecta a los inventarios con coordenadas configuradas - los puramente virtuales, abiertos programáticamente por tu propio script, nunca se precargan. Aun así, escribe el callback como una comprobación pura de trabajo/banda/identificador siempre que puedas. Un patrón de token de un solo uso (`authorized[source] = inventoryId`, consumido en la primera coincidencia) es propenso a condiciones de carrera con un inventario colocado físicamente: una precarga puede consumir el token antes de que la apertura real llegue al hook, y entonces la apertura se deniega.

<Warning>
  El mensaje devuelto por este hook no se muestra al jugador, porque la precarga haría que se repitiese. Llama a `notifyPlayer` desde dentro del hook si quieres decirle al jugador el motivo.
</Warning>

### Cosas a tener en cuenta

<AccordionGroup>
  <Accordion title="Stashes privados">
    jaksam añade `_<ownerCharIdentifier>` a los IDs de los stashes privados, así que `payload.inventoryId` es el ID ya resuelto. Los patrones basados en prefijo siguen coincidiendo, ya que el sufijo va al final.
  </Accordion>

  <Accordion title="Contenedores">
    Bloquear un contenedor solo impide que se abra. Soltar un ítem sobre una mochila cerrada sigue funcionando, porque eso es una transferencia de ítem - usa [`onItemTransferred`](/es/jaksam-inventory/hooks/on-item-transferred) para restringir lo que entra.
  </Accordion>

  <Accordion title="forceOpenInventory sigue activando este hook">
    `forceOpenInventory` se salta las comprobaciones de permisos propias de jaksam, pero no tus hooks - igual que ox_inventory, cuyo hook `openInventory` se dispara incluso cuando `forceOpenInventory` pasa `ignoreSecurityChecks`. Esto significa que un hook también puede bloquear un `/openinventory` de admin, `OpenInventoryById` o `forceOpenInventoryOX`, así que filtra por los inventarios que realmente te interesan en lugar de denegar por defecto.
  </Accordion>
</AccordionGroup>

### Ejemplos

<AccordionGroup>
  <Accordion title="Restringir los stashes de trabajo a su propio trabajo">
    ```lua
    -- Comprobación sin estado: segura aunque se repita durante la precarga
    exports['jaksam_inventory']:registerHook("onPreOpenInventory", function(payload)
        local job = payload.inventoryId:match("^job_stash_(.+)$")
        if job and GetPlayerJob(payload.playerId) ~= job then
            return false
        end
    end, {
        inventoryTypeFilter = {stash = true}
    })
    ```
  </Accordion>
</AccordionGroup>

Consulta [Descripción general de Hooks](/es/jaksam-inventory/hooks) para la API de `registerHook`, los filtros disponibles y el comportamiento de los valores de retorno.
