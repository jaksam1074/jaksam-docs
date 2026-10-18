---
title: "Document issued"
description: "Se activa en el servidor después de expedir un documento real."
icon: "id-card"
---

Este evento se activa después de expedir un documento real: en una oficina ciudadana, como documento inicial, por esx_dmvschool o el ayuntamiento, por el comando de admin o por el export [Issue](/es/jaksam-identity/server/register/issue).

<CodeGroup>

```lua Event
AddEventHandler("jksm_identity:issued", function(serial, typeId, targetSrc, issuerSrc)

end)
```

```lua Example
AddEventHandler("jksm_identity:issued", function(serial, typeId, targetSrc, issuerSrc)
    if typeId == "weapon" then
        print(("Player %d received firearms permit %s"):format(targetSrc, serial))
    end
end)
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `serial` | string | El nuevo número de documento |
| `typeId` | string | El tipo de documento, una clave de `Config.Documents` |
| `targetSrc` | integer | ID de servidor del jugador que lo recibió |
| `issuerSrc` | integer \| nil | ID de servidor del jugador que lo expidió, `0` para la consola, **nil** cuando no lo expidió nadie (oficina, documento inicial) |

<Tip>
  Los mismos argumentos llegan a `Editable.OnIssued` en `editable/server.lua`, si prefieres tener tu código ahí.
</Tip>
