---
title: "Darf ausstellen"
description: "Entscheiden, wer einem Spieler ein echtes Dokument ausstellen darf."
icon: "user-check"
---

Wird bei jeder Ausstellung mit Aussteller aufgerufen: dem Admin-Befehl und dem Export [Ausstellen](/de/jaksam-identity/server/register/issue) mit `issuerSrc`. Nicht aufgerufen für Ämter, Starter-Dokumente oder die Konsole. Gib `false` zurück, um die Ausstellung zu blockieren (sie scheitert mit `not_allowed`).

Bearbeite `Editable.CanIssue` in `editable/server.lua`:

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

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `issuerSrc` | integer | Server-ID des Spielers, der es ausstellt |
| `targetSrc` | integer | Server-ID des Spielers, der es bekommt |
| `typeId` | string | Der Dokumenttyp, ein Schlüssel von `Config.Documents` |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `allowed` | boolean | **true**, um die Ausstellung zu erlauben |
