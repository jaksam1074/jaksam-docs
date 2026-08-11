---
title: "Register stash"
description: "Registriert dynamisch einen neuen Stash und erstellt dessen Server-Inventar zur Laufzeit."
icon: "warehouse"
---

Registriert dynamisch einen neuen Stash und erstellt dessen Server-Inventar zur Laufzeit.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerStash(options)
```

```lua Example
-- Einen öffentlichen Stash mit Interaktionspunkt erstellen (runtimeOnly = false)
local stashId = exports['jaksam_inventory']:registerStash({
    label = "Public Storage",
    coords = vector3(100.0, 200.0, 30.0),
    maxWeight = 500,
    maxSlots = 50,
    radius = 5.0,
    runtimeOnly = false -- Interaktionspunkte aktivieren
})

-- Einen job-eingeschränkten Stash mit Interaktionspunkt erstellen
local policeStashId = exports['jaksam_inventory']:registerStash({
    id = "police_evidence",
    label = "Police Evidence Locker",
    coords = vector3(450.0, -990.0, 30.0),
    maxWeight = 1000,
    maxSlots = 100,
    radius = 3.0,
    allowedJobs = {police = true, sheriff = true},
    runtimeOnly = false -- Interaktionspunkte aktivieren
})

-- Einen rein programmatischen Stash erstellen (Standardverhalten, runtimeOnly = true)
-- Spieler können nicht per Weltinteraktion darauf zugreifen, nur per Code
local hiddenStashId = exports['jaksam_inventory']:registerStash({
    id = "secret_stash",
    label = "Secret Storage",
    maxWeight = 200,
    maxSlots = 30
    -- Keine Koordinaten angegeben, nur programmatischer Zugriff
})

-- Einen privaten Stash erstellen (jeder Spieler bekommt beim Zugriff sein eigenes Inventar)
local privateStashId = exports['jaksam_inventory']:registerStash({
    id = "luxury_apartment_stash",
    label = "Personal Safe",
    coords = vector3(300.0, 400.0, 50.0),
    maxWeight = 200,
    maxSlots = 30,
    isPrivate = true
})

-- Einen temporären Stash mit Startitems erstellen (wird nicht in der Datenbank gespeichert)
local tempStashId = exports['jaksam_inventory']:registerStash({
    label = "Event Loot Box",
    coords = vector3(500.0, 600.0, 20.0),
    maxWeight = 100,
    maxSlots = 20,
    temporary = true,
    startingItems = {
        {"bread", 5, nil},
        {"water", 3, nil},
        {"money", 1000, nil}
    }
})

-- Einen menübasierten Stash erstellen (runtimeOnly = true standardmäßig)
-- Nützlich für eigene UI-/Menüsysteme
local virtualStashId = exports['jaksam_inventory']:registerStash({
    id = "player_bank_vault",
    label = "Bank Vault",
    maxWeight = 500,
    maxSlots = 50,
    isPrivate = true
    -- runtimeOnly = true standardmäßig, nur programmatischer Zugriff
})

-- Stash programmatisch vom Server öffnen (z.B. aus einem Menü oder Befehl)
RegisterCommand('openvault', function(source)
    local charId = Framework.getPlayerCharIdentifier(source)
    local stashId = "player_bank_vault_" .. charId
    exports['jaksam_inventory']:forceOpenInventory(source, stashId)
end)

-- Alternative: Vom Client-Script aus öffnen
-- exports['jaksam_inventory']:openInventory('stashId')
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `options` | table | Konfigurationstabelle für den Stash (siehe Hinweise unten) |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `stashId` | string \| nil | Die ID des erstellten Stashs, nil falls die Erstellung fehlgeschlagen ist |

### Hinweise

`options`-Felder:

- `id` (string, optional): Eindeutige ID für den Stash. Falls nicht angegeben, wird eine automatisch generiert
- `label` (string, erforderlich): Anzeigename für den Stash
- `coords` (vector3 \| table, optional): Ort, über den der Stash per Interaktionspunkt erreichbar ist
- `maxWeight` (number, optional): Maximale Gewichtskapazität. Standard: 100
- `maxSlots` (number, optional): Maximale Anzahl an Slots. Standard: 100
- `radius` (number, optional): Entfernung, aus der Spieler auf den Stash zugreifen können. Standard: 3.0
- `isPrivate` (boolean, optional): Bei true wird für jeden Spieler ein eigenes Inventar erstellt. Standard: false
- `allowedJobs` (table, optional): Tabelle der Jobs, die auf den Stash zugreifen dürfen. Bei nil ist der Stash öffentlich
- `temporary` (boolean, optional): Bei true wird der Stash nicht in der Datenbank gespeichert und geht beim Script-Neustart verloren. Standard: false
- `startingItems` (table, optional): Items, die beim ersten Erstellen des Stashs hinzugefügt werden. Format: `{{itemName, amount, metadata}, ...}`
- `runtimeOnly` (boolean, optional): Bei true (Standard) kann der Stash nur programmatisch geöffnet werden. Bei false und angegebenen Koordinaten werden client-seitige Interaktionspunkte erstellt. Standard: true
