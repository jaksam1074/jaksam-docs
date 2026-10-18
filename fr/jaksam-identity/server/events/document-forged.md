---
title: "Document falsifié"
description: "Déclenché côté serveur après la fabrication d'un faux."
icon: "print"
---

Cet event est déclenché après la fabrication d'un faux, par un joueur, un ouvrier PNJ ou la commande admin.

<CodeGroup>

```lua Event
AddEventHandler("jksm_identity:forged", function(serial, typeId, quality, forgerId)

end)
```

```lua Example
AddEventHandler("jksm_identity:forged", function(serial, typeId, quality, forgerId)
    if quality >= 90 then
        print(("A near perfect %s was forged (%s)"):format(typeId, serial))
    end
end)
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `serial` | string | Le numéro du faux |
| `typeId` | string | Le type de document, une clé de `Config.Documents` |
| `quality` | integer | La qualité, de 0 à 100 |
| `forgerId` | string \| nil | L'identifier du personnage faussaire, `'console'` ou **nil** |

<Tip>
  Les mêmes arguments arrivent à `Editable.OnForged` dans `editable/server.lua`, si tu préfères garder ton code là.
</Tip>
