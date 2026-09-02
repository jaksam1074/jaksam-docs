---
title: "Pre open inventory"
description: "Hook, der ausgelöst wird, bevor ein sekundäres Inventar an den Client gesendet wird, und das Öffnen verhindern kann."
icon: "door-open"
---

Wird ausgelöst, BEVOR ein sekundäres Inventar (Stash, Kofferraum, Handschuhfach, Shop, Drop, Container, das Inventar eines anderen Spielers, ...) an den Client gesendet wird. Dieser Hook kann das Öffnen des Inventars verhindern. Registriere mit [`registerHook`](/de/jaksam-inventory/hooks#einen-hook-registrieren) unter dem Event-Namen `onPreOpenInventory`.

Das Öffnen des **eigenen** Spieler-Inventars löst diesen Hook nie aus.

### Payload

| Feld | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | number | Der Spieler, der das Inventar öffnet |
| `inventoryId` | string | z.B. `"stash_07ABC"` |
| `inventoryType` | string | `player`, `stash`, `shop`, `trunk`, `glovebox`, `container`, `ground_container`, `dumpster`, `omnipack` |
| `slotId` | number \| nil | Nur bei Containern: der Slot des Container-Items im übergeordneten Inventar |

<Note>
  Dieser Hook kann das Öffnen des Inventars durch `return false` verhindern. Die Daten verlassen den Server nie, es ist also eine echte Zugriffskontrolle (Job-/Gang-/Whitelist-Prüfung), nicht nur eine UI-Prüfung.
</Note>

**Verfügbare Filter:** `inventoryTypeFilter` und `inventoryFilter`.

### Bevorzuge zustandslose Hooks

Wenn ein Spieler die Inventar-Taste drückt, lädt der Client die Inventare in Reichweite vor (Stashes innerhalb von 3m einer konfigurierten Position, dazu nahe Kofferräume, Handschuhfächer, Shops, Mülleimer und Drops), bevor die UI öffnet, und jedes Vorladen löst diesen Hook aus. Dein Callback kann daher mehrmals für dasselbe Inventar laufen, und auch für Inventare, die der Spieler nie tatsächlich öffnet.

Das betrifft nur Inventare mit konfigurierten Koordinaten - rein virtuelle, die von deinem eigenen Script programmatisch geöffnet werden, werden nie vorgeladen. Schreibe das Callback trotzdem nach Möglichkeit als reine Prüfung auf Job/Gang/Identifier. Ein One-Shot-Token-Muster (`authorized[source] = inventoryId`, beim ersten Treffer verbraucht) ist bei einem physisch platzierten Inventar anfällig für Race Conditions: Ein Vorladen kann das Token verbrauchen, bevor das echte Öffnen den Hook erreicht, und das Öffnen wird dann abgelehnt.

<Warning>
  Die von diesem Hook zurückgegebene Nachricht wird dem Spieler nicht angezeigt, weil das Vorladen sie wiederholen würde. Rufe `notifyPlayer` innerhalb des Hooks auf, wenn du dem Spieler den Grund mitteilen möchtest.
</Warning>

### Wissenswertes

<AccordionGroup>
  <Accordion title="Private Stashes">
    jaksam hängt `_<ownerCharIdentifier>` an die IDs privater Stashes an, `payload.inventoryId` ist also die vollständig aufgelöste ID. Präfix-basierte Muster passen weiterhin, da das Suffix am Ende steht.
  </Accordion>

  <Accordion title="Container">
    Einen Container zu blockieren verhindert nur, dass er geöffnet wird. Ein Item auf einen geschlossenen Rucksack zu ziehen funktioniert weiterhin, denn das ist eine Item-Übertragung - nutze [`onItemTransferred`](/de/jaksam-inventory/hooks/on-item-transferred), um einzuschränken, was hineinkommt.
  </Accordion>

  <Accordion title="forceOpenInventory löst diesen Hook weiterhin aus">
    `forceOpenInventory` überspringt die eigenen Berechtigungsprüfungen von jaksam, aber nicht deine Hooks - genau wie bei ox_inventory, dessen `openInventory`-Hook auch dann feuert, wenn `forceOpenInventory` `ignoreSecurityChecks` übergibt. Das bedeutet, dass ein Hook auch ein Admin-`/openinventory`, `OpenInventoryById` oder `forceOpenInventoryOX` blockieren kann, filtere also auf die Inventare, die dich wirklich interessieren, statt standardmäßig alles abzulehnen.
  </Accordion>
</AccordionGroup>

### Beispiele

<AccordionGroup>
  <Accordion title="Job-Stashes auf den eigenen Job beschränken">
    ```lua
    -- Zustandslose Prüfung: sicher, auch wenn sie beim Vorladen mehrfach läuft
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

Siehe [Hooks-Übersicht](/de/jaksam-inventory/hooks) für die `registerHook`-API, verfügbare Filter und das Rückgabewert-Verhalten.
