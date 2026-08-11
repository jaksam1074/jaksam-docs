---
title: "Optimierung"
description: "Die Item-Events deines Inventars nutzen, um die Performance von Trackers Creator zu verbessern."
icon: "gauge-high"
---

Diese Seite zeigt dir, wie du das Script optimierst. Befolgst du alle Anweisungen unten, verbessert das die Performance des Scripts.

## Item-Prüfung

Nutze diese **serverseitigen** Events direkt nach jedem Hinzufügen/Entfernen von Items. Sie können überall genutzt werden, solange du die Parameter durch die passenden ersetzt.

```lua
TriggerEvent("framework:onItemAdded", playerId, itemName, itemCount)
```

```lua
TriggerEvent("framework:onItemRemoved", playerId, itemName, itemCount)
```

### Beispiele

<Note>
  Nutzt du etwas, das nicht in den Beispielen aufgeführt ist, liegt die Anpassung bei dir, die oben genannten Events funktionieren überall, wenn sie richtig genutzt werden.
</Note>

#### ESX

<Info>
  Standard-ESX hat bereits `esx:onAddInventoryItem` und `esx:onRemoveInventoryItem`, du musst also nichts hinzufügen. Folge dem Beispiel unten nur, falls du diese Events aus irgendeinem Grund nicht hast.
</Info>

Gehe zu `es_extended/server/classes/player.lua` und füge folgenden Code hinzu:

<Frame>
  ![ESX item added/removed hook example 1](/images/immagine-2-1.png)
</Frame>

<Frame>
  ![ESX item added/removed hook example 2](/images/immagine-3.png)
</Frame>

#### OX Inventory (ESX)

Gehe zu `es_extended/server/classes/overrides/oxinventory.lua` und füge folgenden Code hinzu:

<Frame>
  ![OX Inventory hook example 1](/images/immagine-4-1.png)
</Frame>

<Frame>
  ![OX Inventory hook example 2](/images/immagine.png)
</Frame>

#### QBCore (neueste Version)

Gehe zu `qb-inventory/server/main.lua` und füge folgenden Code hinzu:

<Frame>
  ![QBCore hook example 1](/images/immagine-5-1.png)
</Frame>

<Frame>
  ![QBCore hook example 2](/images/immagine-6.png)
</Frame>
