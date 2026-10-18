---
title: "Issue"
description: "Expide un documento real a un jugador y lo pone en su inventario."
icon: "id-card"
---

Expide un documento real: lo escribe en el registro, hace la foto, pone el item en el inventario del jugador y marca como `replaced` el documento válido más antiguo del mismo tipo.

<CodeGroup>

```lua Export
exports["jksm_identity"]:Issue(playerId, typeId, options)
```

```lua Example
-- A DMV script issuing the driver licence after a passed test
local serial, reason = exports["jksm_identity"]:Issue(playerId, "drive", {
    issuerSrc = instructorId,
    grant = { "drive" },
})

if serial then
    print("Issued driver licence " .. serial)
else
    print("Not issued: " .. reason)
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `playerId` | integer | ID de servidor del jugador que recibe el documento |
| `typeId` | string | El tipo de documento, una clave de `Config.Documents` (por ejemplo `id_card`, `drive`, `weapon`, `badge_pd`) |
| `options` | table (opcional) | Mira abajo |

### Opciones

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `issuerSrc` | integer | ID de servidor del jugador que lo expide. Primero se pregunta a `Editable.CanIssue`, y el emisor se escribe en el registro. `0` es la consola |
| `grant` | table | Tipos de licencia que se dan al personaje antes de expedir, por ejemplo `{ "drive", "drive_truck" }`. Deben ser licencias de este documento |
| `force` | boolean | Expide aunque falte la licencia (documentos `license`) o el trabajo (documentos `badge`) |
| `photo` | boolean | `false` para expedir sin hacer foto |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `serial` | string \| nil | El nuevo número de documento, o **nil** si no se expidió |
| `reason` | string \| nil | Por qué no se expidió: `unknown_type`, `no_player`, `not_allowed`, `license_missing`, `wrong_job`, `busy` (se está haciendo una foto de este jugador), `additem_<code>` (el inventario rechazó el item) |

<Note>
  La foto se hace al personaje del jugador, así que la llamada espera por ella. Llámala desde un thread o un event handler, no desde código que deba volver al instante.
</Note>
