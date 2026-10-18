---
title: "Dokumente abrufen"
description: "Alle Registereinträge eines Charakters abrufen, die neuesten zuerst."
icon: "list"
---

Liefert die Registereinträge eines Charakters (nur echte Dokumente), die neuesten zuerst.

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

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `identifier` | string | Der Charakter-Identifier. **In QBCore und Qbox ist das die Citizen-ID** |

### Rückgabewert

Eine Liste von Tabellen, leer, wenn der Charakter keine Dokumente hat:

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `serial` | string | Die Dokumentnummer |
| `doc_type` | string | Der Dokumenttyp, ein Schlüssel von `Config.Documents` |
| `firstname`, `lastname`, `dob`, `sex` | string | Die gedruckte Identität |
| `classes` | string | Die gedruckten Lizenzklassen, zum Beispiel `A, B` |
| `rank` | string | Nur Dienstausweise: der gedruckte Rang |
| `issued_at`, `expires_at` | integer | Unix-Zeiten. `expires_at` ist **nil** bei Dokumenten, die nie ablaufen |
| `status` | string | `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` oder `revoked` |
| `status_until` | integer | Unix-Zeit, zu der eine Sperre endet |
| `status_note` | string | Die mit dem Status gespeicherte Notiz |
