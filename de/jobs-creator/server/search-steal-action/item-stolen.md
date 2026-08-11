---
title: "Item gestohlen"
description: "Wird ausgelöst, nachdem ein Spieler etwas über das Actions-Menü gestohlen hat, nur bei Verwendung der Standard-Player-Search/-Rob, funktioniert nicht, wenn diese ersetzt wurde"
icon: "hand"
---

Wird ausgelöst, nachdem ein Spieler etwas über das Actions-Menü gestohlen hat.

<Note>
  Dies funktioniert nur, wenn du die Standard-Player-Search-/Rob-Action verwendest — es wird nicht ausgelöst, wenn du sie durch ein eigenes Modul ersetzt hast.
</Note>

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:actions:itemStolen", function(playerId, targetId, itemName, itemQuantity)
end)
```

```lua Beispiel
-- Dieses Beispiel für ESX "löscht" alle gestohlenen Items
RegisterNetEvent("jobs_creator:actions:itemStolen", function(playerId, targetId, itemName, itemQuantity)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    xPlayer.removeInventoryItem(itemName, itemQuantity)
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers, der das Item gestohlen hat |
| `targetId` | integer | Server-ID des Opfers, das das Item verloren hat |
| `itemName` | string | Item-Name |
| `itemQuantity` | integer | Gestohlene Menge |
