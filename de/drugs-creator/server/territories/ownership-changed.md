---
title: "Besitzer geändert"
description: "Wird server-seitig ausgelöst, wenn ein Territorium den Besitzer wechselt."
icon: "flag"
---

Wird server-seitig ausgelöst, wenn ein Territorium den Besitzer wechselt.

```lua Event
AddEventHandler("drugs_creator:territories:ownershipChanged", function(territoryName, newOwner, previousOwner)

end)
```

### Parameter

| Name              | Datentyp    | Beschreibung                                           |
| ------------------ | ------------- | ----------------------------------------------------------- |
| `territoryName`     | string        | Der Name des Territoriums, das den Besitzer gewechselt hat                   |
| `newOwner`          | string / nil  | Der Job-/Gang-Name des neuen Besitzers, oder `nil`, falls verloren              |
| `previousOwner`     | string / nil  | Der Job-/Gang-Name des vorherigen Besitzers, oder `nil`                  |

## Beispiel

```lua
AddEventHandler("drugs_creator:territories:ownershipChanged", function(territoryName, newOwner, previousOwner)
    if newOwner then
        print(("%s is now owned by %s (was: %s)"):format(territoryName, newOwner, previousOwner or "nobody"))
    else
        print(("%s has been lost by %s"):format(territoryName, previousOwner or "unknown"))
    end
end)
```
