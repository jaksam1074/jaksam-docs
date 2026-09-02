---
title: "Omnipack transaction"
description: "Hook, der ausgelöst wird, wenn ein Admin über das Admin-Inventar (Omnipack) ein Item erstellt oder zerstört."
icon: "user-shield"
---

Wird ausgelöst, wenn ein Admin ein Item aus dem [Admin-Inventar (Omnipack)](/de/jaksam-inventory/guides/admin-inventory) herausnimmt, wodurch es erstellt wird, oder eines hineinzieht, wodurch es zerstört wird. Dieser Hook kann den Vorgang abbrechen. Registriere mit [`registerHook`](/de/jaksam-inventory/hooks#einen-hook-registrieren) unter dem Event-Namen `onOmnipackTransaction`.

Es ist der einzige Hook, der weiß, **welcher** Admin es getan hat, also der richtige, um das Spawnen von Items durch Admins zu loggen.

### Payload

| Feld | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | number | Der Admin, der das Admin-Inventar benutzt |
| `action` | string | `"spawn"` (Item erstellt) oder `"delete"` (Item zerstört) |
| `inventoryId` | string | Das andere Inventar: wohin das Item geht oder woher es kommt |
| `slotId` | number | Der betroffene Slot im anderen Inventar |
| `itemName` | string | z.B. `"weapon_pistol"` |
| `amount` | number | Erstellte oder zerstörte Menge |
| `metadata` | table \| nil | Item-Metadaten |

<Note>
  Das Admin-Inventar löst **nicht** [`onItemTransferred`](/de/jaksam-inventory/hooks/on-item-transferred) aus, sondern nur diesen Hook. So werden die Einschränkungen, die du für deine Spieler schreibst, nie auf einen Admin angewendet, der ein Item spawnt.
</Note>

**Verfügbare Filter:** `itemNameFilter`, `itemTypeFilter`, `inventoryTypeFilter` und `inventoryFilter` - die letzten beiden beziehen sich auf `inventoryId`, das Omnipack selbst ist also nie das, worauf du filterst.

### Beispiele

<AccordionGroup>
  <Accordion title="Loggen, was Admins aus dem Admin-Inventar spawnen">
    ```lua
    exports['jaksam_inventory']:registerHook("onOmnipackTransaction", function(payload)
        print(("[ADMIN] %s (%s) %sed %dx %s - inventory: %s"):format(
            GetPlayerName(payload.playerId), payload.playerId, payload.action,
            payload.amount, payload.itemName, payload.inventoryId))
    end)
    ```
  </Accordion>

  <Accordion title="Admins daran hindern, ein bestimmtes Item zu spawnen">
    ```lua
    exports['jaksam_inventory']:registerHook("onOmnipackTransaction", function(payload)
        if payload.action ~= "spawn" then return end -- Löschen ist in Ordnung

        return false, "This item can't be spawned from the admin inventory"
    end, {
        itemNameFilter = {money = true}
    })
    ```
  </Accordion>
</AccordionGroup>

Siehe [Hooks-Übersicht](/de/jaksam-inventory/hooks) für die `registerHook`-API, verfügbare Filter und das Rückgabewert-Verhalten.
