---
title: "Get documents"
description: "Get all the register records of a character, newest first."
icon: "list"
---

Returns the register records of a character (real documents only), newest first.

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `identifier` | string | The character identifier. **In QBCore and Qbox it's the citizen ID** |

### Return value

A list of tables, empty if the character has no documents:

| Name | Data Type | Description |
| --- | --- | --- |
| `serial` | string | The document number |
| `doc_type` | string | The document type, a key of `Config.Documents` |
| `firstname`, `lastname`, `dob`, `sex` | string | The printed identity |
| `classes` | string | The printed licence classes, for example `A, B` |
| `rank` | string | Badges only: the printed rank |
| `issued_at`, `expires_at` | integer | Unix times. `expires_at` is **nil** for documents that never expire |
| `status` | string | `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` or `revoked` |
| `status_until` | integer | Unix time a suspension ends |
| `status_note` | string | The note stored with the status |
