---
title: "Can issue"
description: "Decide quién puede expedir un documento real a un jugador."
icon: "user-check"
---

Se llama en cada expedición que tiene emisor: el comando de admin y el export [Issue](/es/jaksam-identity/server/register/issue) con `issuerSrc`. No se llama para oficinas, documentos iniciales ni la consola. Devuelve `false` para bloquear la expedición (falla con `not_allowed`).

Edita `Editable.CanIssue` en `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.CanIssue(issuerSrc, targetSrc, typeId)
    return true
end
```

```lua Example
-- Only police officers may issue firearms permits (ESX)
function Editable.CanIssue(issuerSrc, targetSrc, typeId)
    if typeId == "weapon" then
        return ESX.GetPlayerFromId(issuerSrc).getJob().name == "police"
    end
    return true
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `issuerSrc` | integer | ID de servidor del jugador que lo expide |
| `targetSrc` | integer | ID de servidor del jugador que lo recibe |
| `typeId` | string | El tipo de documento, una clave de `Config.Documents` |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `allowed` | boolean | **true** para permitir la expedición |
