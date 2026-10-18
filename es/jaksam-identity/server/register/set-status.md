---
title: "Set status"
description: "Cambia el estado en el registro de un documento real: perdido, robado, retirado, suspendido, sustituido, revocado o válido."
icon: "tag"
---

Fija el estado en el registro de un documento real. El cambio queda en el log y activa el evento [Status changed](/es/jaksam-identity/server/events/status-changed).

<CodeGroup>

```lua Export
exports["jksm_identity"]:SetStatus(serial, status, options)
```

```lua Example
-- Suspend a driver licence for 7 days from an MDT
local ok, reason = exports["jksm_identity"]:SetStatus("SAAB1234567", "suspended", {
    untilTime = os.time() + 7 * 24 * 60 * 60,
    note = "Speeding, 7 days",
    actor = officerIdentifier,
})

if not ok then print("Failed: " .. reason) end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `serial` | string | El número del documento |
| `status` | string | `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` o `revoked` |
| `options` | table (opcional) | Mira abajo |

### Opciones

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `untilTime` | integer | Solo con `suspended`: tiempo unix en que termina la suspensión. Después la consulta del registro vuelve a devolver `valid` |
| `note` | string | Una nota que se guarda con el estado (hasta 255 caracteres) |
| `actor` | string | Quién lo cambió, se escribe en el log de admin |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `ok` | boolean | **true** si el estado se cambió |
| `reason` | string \| nil | `bad_arguments` o `not_found` (el número no es un documento real) |
