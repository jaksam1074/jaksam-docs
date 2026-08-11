---
title: "Pre use item"
description: "Hook, der vor der Nutzung eines Items ausgelöst wird, kann die Nutzung abbrechen."
icon: "hand"
---

Wird VOR der Nutzung eines Items ausgelöst (vor Verbrauch, Animationen und Verzögerungen). Dieser Hook kann die Item-Nutzung abbrechen. Registriere mit [`registerHook`](/de/jaksam-inventory/hooks#register-a-hook) unter dem Event-Namen `onPreUseItem`.

**Ausführungsreihenfolge:** nach `STATIC_ITEM.canUse` und `oxServerExport 'usingItem'`, vor dem Verbrauch.

### Payload

| Feld | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | number | Der Spieler, der das Item benutzt |
| `inventoryId` | string | z.B. `"license:abcd1234"` |
| `slotId` | number | Slot des benutzten Items |
| `itemName` | string | z.B. `"bread"` |
| `metadata` | table \| nil | Item-Metadaten |

<Note>
  Dieser Hook kann die Item-Nutzung verhindern, indem er `false` zurückgibt. Nützlich für globale Nutzungseinschränkungen (z.B. gefesselte Spieler, Fahrzeugbeschränkungen, Zonenbeschränkungen).
</Note>

### Beispiele

<AccordionGroup>
  <Accordion title="Item-Nutzung blockieren, wenn gefesselt">
    ```lua
    exports['jaksam_inventory']:registerHook("onPreUseItem", function(payload)
        if IsPlayerHandcuffed(payload.playerId) then
            return false, "You cannot use items while handcuffed"
        end
    end)
    ```
  </Accordion>

  <Accordion title="Essen im Fahrzeug blockieren">
    ```lua
    exports['jaksam_inventory']:registerHook("onPreUseItem", function(payload)
        local ped = GetPlayerPed(payload.playerId)
        if IsPedInAnyVehicle(ped, false) then
            return false, "You cannot eat while driving", "warning"
        end
    end, {
        itemTypeFilter = {food = true}
    })
    ```
  </Accordion>
</AccordionGroup>

Siehe [Hooks-Übersicht](/de/jaksam-inventory/hooks) für die `registerHook`-API, verfügbare Filter und das Rückgabewert-Verhalten.
