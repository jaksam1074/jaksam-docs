---
title: "Status changed"
description: "Se activa en el servidor después de que cambie el estado en el registro de un documento real."
icon: "tag"
---

Este evento se activa después de que cambie el estado en el registro de un documento real, por ejemplo cuando se denuncia como robado en una oficina o se suspende con el export [Set status](/es/jaksam-identity/server/register/set-status).

<CodeGroup>

```lua Event
AddEventHandler("jksm_identity:statusChanged", function(serial, status, previous)

end)
```

```lua Example
AddEventHandler("jksm_identity:statusChanged", function(serial, status, previous)
    if status == "stolen" then
        -- flag it in your MDT
        exports["my_mdt"]:AddFlag(serial, "Reported stolen")
    end
end)
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `serial` | string | El número del documento |
| `status` | string | El nuevo estado: `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` o `revoked` |
| `previous` | string | El estado anterior |
