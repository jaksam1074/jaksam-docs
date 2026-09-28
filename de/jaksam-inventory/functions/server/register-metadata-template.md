---
title: "Register metadata template"
description: "Fügt ein Metadata-Template aus einem externen Script hinzu, das von Items mit dynamischen Metadaten verwendet wird."
icon: "tags"
---

Fügt ein Metadata-Template aus einem externen Script hinzu. Ein Metadata-Template ist eine Funktion, die jedes Mal einen Metadaten-Wert erzeugt, wenn ein Item, das es verwendet, einem Inventar hinzugefügt wird (eine Seriennummer, der Name des Besitzers, ein zufälliger Wert usw.).

So registrierte Templates funktionieren genau wie die in `metadata_templates.lua`: Sie erscheinen im Item-Editor des Admin-Menüs `/inventory`, wo du sie jedem Item zuweisen kannst. Wie Templates Items zugewiesen werden, steht im [Metadata-Guide](/de/jaksam-inventory/guides/metadata).

<Note>
  Templates werden nur im Speicher gehalten. Sie werden entfernt, wenn dein Script stoppt, und gehen verloren, wenn jaksam_inventory neu startet. Registriere sie also bei jedem Start deines Scripts.
</Note>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerMetadataTemplate(templateId, cb)
```

```lua Example
local function registerTemplates()
    exports['jaksam_inventory']:registerMetadataTemplate('my_serial', function(playerId, inventoryId, itemName, amount, metadata, slotId)
        return 'SN-' .. math.random(100000, 999999)
    end)
end

-- Beim Start registrieren, und erneut, falls jaksam_inventory nach deinem Script neu gestartet wird
registerTemplates()

AddEventHandler('onResourceStart', function(resourceName)
    if resourceName == 'jaksam_inventory' then registerTemplates() end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `templateId` | string | Die ID des Templates, die du im Item-Editor auswählst |
| `cb` | function | Wird jedes Mal aufgerufen, wenn ein Item mit diesem Template hinzugefügt wird. Der Rückgabewert wird zum Metadaten-Wert |

#### Parameter des Callbacks

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | number \| nil | Server-ID des Spielers, nur wenn das Item einem Spielerinventar hinzugefügt wird |
| `inventoryId` | string | Das Inventar, dem das Item hinzugefügt wird |
| `itemName` | string | Das hinzugefügte Item |
| `amount` | number | Die hinzugefügte Menge |
| `metadata` | table \| nil | Die Metadaten, mit denen das Item hinzugefügt wird |
| `slotId` | string \| nil | Der Slot, in den das Item gelegt wird, falls einer angegeben wurde |

### Rückgabewert

Keiner

### Hinweise

- Nur serverseitig, da Metadaten immer vom Server erzeugt werden
- Hat dein Template dieselbe ID wie eines in `metadata_templates.lua`, ersetzt deines es, solange dein Script läuft, und das ursprüngliche kommt zurück, wenn dein Script stoppt
- Solange ein Template nicht registriert ist (dein Script ist noch nicht gestartet oder wurde gestoppt), werden Items, die es verwenden, normal hinzugefügt, nur ohne dieses Metadaten-Feld, und die Server-Konsole zeigt eine Warnung
