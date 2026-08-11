---
title: "Pocket-Crafting abgeschlossen"
description: "Wird server-seitig ausgelöst, wenn ein Spieler einen Pocket-Crafting-Prozess abschließt."
icon: "flask-vial"
---

Dieses Event wird ausgelöst, nachdem ein Spieler erfolgreich einen Pocket-Crafting-Prozess abgeschlossen hat. Es wird direkt ausgelöst, nachdem der Spieler sein gecraftetes Item erhalten hat.

```lua Event
AddEventHandler("drugs_creator:pocketCraftingFinished", function(playerId, itemName)

end)
```

### Parameter

| Name        | Datentyp | Beschreibung                                                  |
| ----------- | --------- | ------------------------------------------------------------- |
| `playerId`  | integer   | Die Server-ID des Spielers, der das Crafting abgeschlossen hat            |
| `itemName`  | string    | Der Name des genutzten Pocket-Crafting-Items                 |

## Beispiel

```lua
AddEventHandler("drugs_creator:pocketCraftingFinished", function(playerId, itemName)
    print("Player " .. playerId .. " finished crafting with " .. itemName)
end)
```
