---
title: "Status setzen"
description: "Den Register-Status eines echten Dokuments ändern: verloren, gestohlen, eingezogen, gesperrt, ersetzt, entzogen oder gültig."
icon: "tag"
---

Setzt den Register-Status eines echten Dokuments. Die Änderung wird geloggt und löst das Event [Status geändert](/de/jaksam-identity/server/events/status-changed) aus.

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

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `serial` | string | Die Dokumentnummer |
| `status` | string | `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` oder `revoked` |
| `options` | table (optional) | Siehe unten |

### Optionen

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `untilTime` | integer | Nur bei `suspended`: Unix-Zeit, zu der die Sperre endet. Danach liefert die Registerabfrage wieder `valid` |
| `note` | string | Eine Notiz, die mit dem Status gespeichert wird (bis 255 Zeichen) |
| `actor` | string | Wer es geändert hat, wird ins Admin-Log geschrieben |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `ok` | boolean | **true**, wenn der Status geändert wurde |
| `reason` | string \| nil | `bad_arguments` oder `not_found` (die Nummer ist kein echtes Dokument) |
