---
title: "Is inventory open"
description: "Prüft, ob aktuell ein Inventar geöffnet ist."
icon: "door-open"
---

Prüft, ob aktuell ein Inventar geöffnet ist. Wird keine Inventar-ID angegeben, wird zurückgegeben, ob die Inventar-UI aktuell aktiv ist (irgendein Inventar geöffnet). Wird eine Inventar-ID angegeben, wird geprüft, ob dieses bestimmte Inventar geöffnet ist.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:isInventoryOpen(inventoryId)
```

```lua Example
-- Prüfen, ob irgendeine Inventar-UI geöffnet ist
local isAnyInventoryOpen = exports['jaksam_inventory']:isInventoryOpen()

if isAnyInventoryOpen then
    print('An inventory is currently open')
else
    print('No inventory is open')
end

-- Prüfen, ob ein bestimmtes Inventar geöffnet ist
local isPoliceStashOpen = exports['jaksam_inventory']:isInventoryOpen('police_stash_1')

if isPoliceStashOpen then
    print('Police stash is currently open')
end

-- Öffnen einer weiteren UI verhindern, falls das Inventar bereits offen ist
if not exports['jaksam_inventory']:isInventoryOpen() then
    -- Eigene UI öffnen
    TriggerEvent('myScript:openCustomUI')
else
    notify("Can't do it while inventory is open")
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| nil | Die ID des zu prüfenden Inventars. Bei nil wird zurückgegeben, ob irgendeine Inventar-UI aktuell aktiv ist |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isOpen` | boolean | True, falls das Inventar (oder irgendeine Inventar-UI bei inventoryId = nil) geöffnet ist, sonst false |
