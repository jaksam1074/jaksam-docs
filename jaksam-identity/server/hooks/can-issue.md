---
title: "Can issue"
description: "Decide who may issue a real document to a player."
icon: "user-check"
---

Called for every issue that has an issuer: the admin command and the [Issue](/jaksam-identity/server/register/issue) export with `issuerSrc`. Not called for offices, starter documents or the console. Return `false` to block the issue (it fails with `not_allowed`).

Edit `Editable.CanIssue` in `editable/server.lua`:

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `issuerSrc` | integer | Server ID of the player who issues it |
| `targetSrc` | integer | Server ID of the player who receives it |
| `typeId` | string | The document type, a key of `Config.Documents` |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `allowed` | boolean | **true** to allow the issue |
