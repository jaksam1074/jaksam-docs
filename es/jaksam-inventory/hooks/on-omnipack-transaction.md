---
title: "Omnipack transaction"
description: "Hook activado cuando un admin crea o destruye un ítem a través del inventario de admin (omnipack)."
icon: "user-shield"
---

Se activa cuando un admin saca un ítem del [inventario de admin (omnipack)](/es/jaksam-inventory/guides/admin-inventory), lo que lo crea, o arrastra uno dentro, lo que lo destruye. Este hook puede cancelar la operación. Regístralo con [`registerHook`](/es/jaksam-inventory/hooks#registrar-un-hook) usando el nombre de event `onOmnipackTransaction`.

Es el único hook que sabe **qué** admin lo hizo, así que es el que hay que usar para registrar los ítems que los admins crean.

### Payload

| Campo | Tipo de Dato | Descripción |
| --- | --- | --- |
| `playerId` | number | El admin que usa el inventario de admin |
| `action` | string | `"spawn"` (ítem creado) o `"delete"` (ítem destruido) |
| `inventoryId` | string | El otro inventario: a dónde va el ítem, o de dónde viene |
| `slotId` | number | El slot implicado en el otro inventario |
| `itemName` | string | p. ej. `"weapon_pistol"` |
| `amount` | number | Cantidad creada o destruida |
| `metadata` | table \| nil | Metadatos del ítem |

<Note>
  El inventario de admin **no** activa [`onItemTransferred`](/es/jaksam-inventory/hooks/on-item-transferred), solo activa este hook. Así las restricciones que escribes para tus jugadores nunca se aplican a un admin creando un ítem.
</Note>

**Filtros disponibles:** `itemNameFilter`, `itemTypeFilter`, `inventoryTypeFilter` e `inventoryFilter` - los dos últimos se aplican a `inventoryId`, así que el omnipack en sí nunca es lo que filtras.

### Ejemplos

<AccordionGroup>
  <Accordion title="Registrar lo que los admins crean desde el inventario de admin">
    ```lua
    exports['jaksam_inventory']:registerHook("onOmnipackTransaction", function(payload)
        print(("[ADMIN] %s (%s) %sed %dx %s - inventory: %s"):format(
            GetPlayerName(payload.playerId), payload.playerId, payload.action,
            payload.amount, payload.itemName, payload.inventoryId))
    end)
    ```
  </Accordion>

  <Accordion title="Impedir que los admins creen un ítem concreto">
    ```lua
    exports['jaksam_inventory']:registerHook("onOmnipackTransaction", function(payload)
        if payload.action ~= "spawn" then return end -- Borrarlo está bien

        return false, "This item can't be spawned from the admin inventory"
    end, {
        itemNameFilter = {money = true}
    })
    ```
  </Accordion>
</AccordionGroup>

Consulta [Descripción general de Hooks](/es/jaksam-inventory/hooks) para la API de `registerHook`, los filtros disponibles y el comportamiento de los valores de retorno.
