---
title: "Document forged"
description: "Se activa en el servidor después de hacer una falsificación."
icon: "print"
---

Este evento se activa después de hacer una falsificación, por un jugador, un trabajador NPC o el comando de admin.

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

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `serial` | string | El número de la falsificación |
| `typeId` | string | El tipo de documento, una clave de `Config.Documents` |
| `quality` | integer | La calidad, de 0 a 100 |
| `forgerId` | string \| nil | El identificador del personaje falsificador, `'console'` o **nil** |

<Tip>
  Los mismos argumentos llegan a `Editable.OnForged` en `editable/server.lua`, si prefieres tener tu código ahí.
</Tip>
