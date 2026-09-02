---
title: "Item transferred"
description: "Hook activado cuando un ítem se transfiere entre inventarios, incluyendo movimientos dentro del mismo inventario."
icon: "right-left"
---

Se activa cuando un ítem se transfiere entre inventarios (incluyendo movimientos dentro del mismo inventario, p. ej. arrastrar dentro del mismo inventario). Regístralo con [`registerHook`](/es/jaksam-inventory/hooks#registrar-un-hook) usando el nombre de event `onItemTransferred`.

### Payload

| Campo | Tipo de Dato | Descripción |
| --- | --- | --- |
| `playerId` | number | El jugador que realiza la transferencia |
| `inventoryIdFrom` | string | ID del inventario de origen |
| `inventoryIdTo` | string | ID del inventario de destino |
| `slotIdFrom` | number | Slot de origen |
| `slotIdTo` | number | Slot de destino |
| `itemName` | string | p. ej. `"weapon_pistol"` |
| `amount` | number | Cantidad transferida |
| `metadata` | table \| nil | Metadatos del ítem |

<Note>
  El inventario de admin (omnipack) **no** activa este hook, tiene su propio [`onOmnipackTransaction`](/es/jaksam-inventory/hooks/on-omnipack-transaction). Así las restricciones que escribes para tus jugadores nunca se aplican a un admin creando un ítem.
</Note>

### Ejemplos

<AccordionGroup>
  <Accordion title="Bloquear armas policiales en el inventario del jugador">
    ```lua
    exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
        local item = exports["jaksam_inventory"]:getStaticItem(payload.itemName)
        if item and item.policeOnly then
            return false, "Only police can have this weapon"
        end
    end, {
        itemTypeFilter = {weapon = true},
        inventoryToTypeFilter = {player = true}
    })
    ```
  </Accordion>

  <Accordion title="Crafting simple (arrastrar ítems juntos)">
    ```lua
    exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
        local sourceItem = exports["jaksam_inventory"]:getItemFromSlot(payload.inventoryIdFrom, payload.slotIdFrom)
        local targetItem = exports["jaksam_inventory"]:getItemFromSlot(payload.inventoryIdTo, payload.slotIdTo)
        if not targetItem then return end -- Se arrastró sobre un slot vacío

        if sourceItem.name == "bread" and targetItem.name == "meat" then
            exports["jaksam_inventory"]:removeItem(payload.inventoryIdFrom, "bread", 1, payload.slotIdFrom)
            exports["jaksam_inventory"]:removeItem(payload.inventoryIdFrom, "meat", 1, payload.slotIdTo)
            exports["jaksam_inventory"]:addItem(payload.inventoryIdFrom, "sandwich", 1)
            return false, "You crafted a sandwich", "success"
        end
    end, {intraInventoryOnly = true})
    ```
  </Accordion>
</AccordionGroup>

Consulta [Descripción general de Hooks](/es/jaksam-inventory/hooks) para la API de `registerHook`, los filtros disponibles (incluyendo los específicos de transferencia `inventoryFromTypeFilter`/`inventoryToTypeFilter`/`intraInventoryOnly`), y el comportamiento de los valores de retorno.
