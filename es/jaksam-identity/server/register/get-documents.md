---
title: "Get documents"
description: "Obtén todos los registros de un personaje, los más nuevos primero."
icon: "list"
---

Devuelve los registros de un personaje (solo documentos reales), los más nuevos primero.

<CodeGroup>

```lua Export
exports["jksm_identity"]:GetDocuments(identifier)
```

```lua Example
-- ESX
local identifier = ESX.GetPlayerFromId(playerId).identifier
-- QBCore / Qbox
-- local identifier = QBCore.Functions.GetPlayer(playerId).PlayerData.citizenid

for _, document in ipairs(exports["jksm_identity"]:GetDocuments(identifier)) do
    print(document.serial, document.doc_type, document.status)
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `identifier` | string | El identificador del personaje. **En QBCore y Qbox es el citizen ID** |

### Valor de retorno

Una lista de tablas, vacía si el personaje no tiene documentos:

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `serial` | string | El número del documento |
| `doc_type` | string | El tipo de documento, una clave de `Config.Documents` |
| `firstname`, `lastname`, `dob`, `sex` | string | La identidad impresa |
| `classes` | string | Las clases de licencia impresas, por ejemplo `A, B` |
| `rank` | string | Solo placas: el rango impreso |
| `issued_at`, `expires_at` | integer | Tiempos unix. `expires_at` es **nil** en documentos que nunca caducan |
| `status` | string | `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` o `revoked` |
| `status_until` | integer | Tiempo unix en que termina una suspensión |
| `status_note` | string | La nota guardada con el estado |
