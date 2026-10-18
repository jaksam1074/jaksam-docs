---
title: "Prüfen"
description: "Registerabfrage einer Dokumentnummer, wie eine Behörde sie sieht."
icon: "magnifying-glass"
---

Liefert, was eine Behörde sieht, wenn sie ein Dokument im Register prüft. Verrät nie, wer eine Fälschung gemacht hat oder ihre Qualität.

<CodeGroup>

```lua Export
exports["jksm_identity"]:Check(serial, printed)
```

```lua Example
-- MDT lookup of the card a suspect handed over
local result = exports["jksm_identity"]:Check(item.metadata.serial, {
    firstname = item.metadata.firstname,
    lastname = item.metadata.lastname,
    dob = item.metadata.dob,
})

if not result.found then
    print(result.personExists and "Serial does not match this person" or "No such person")
elseif #result.problems > 0 then
    print("Problems: " .. table.concat(result.problems, ", "))
else
    print("Document is valid")
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `serial` | string | Die Dokumentnummer |
| `printed` | table (optional) | Was auf der Karte gedruckt ist: `{ firstname, lastname, dob }`. Dient dazu, eine falsche Nummer von einer nicht existierenden Person zu unterscheiden und gedruckte Daten zu erkennen, die vom Register abweichen |

### Rückgabewert

Eine Tabelle:

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `found` | boolean | **true**, wenn die Nummer im Register steht (ein echtes Dokument) |
| `personExists` | boolean | Nur wenn `found` **false** ist: ob ein Charakter mit dem gedruckten Namen existiert |
| `status` | string | Nur wenn gefunden: `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` oder `revoked`. Eine beendete Sperre liefert `valid` |
| `problems` | table | Liste von Strings, leer, wenn alles in Ordnung ist (siehe unten) |
| `record` | table | Nur wenn gefunden: die Register-Zeile (`serial`, `doc_type`, `owner`, `firstname`, `lastname`, `dob`, `sex`, `classes`, `issued_at`, `expires_at`, `status`, `status_until`, `status_note`, ...) |
| `currentClasses` | string | Nur bei Dokumenten mit Lizenzklassen: die Klassen, die der Besitzer jetzt hat, zum Beispiel `A, B` |

### Probleme

| Problem | Bedeutung |
| --- | --- |
| `person_not_found` | Nicht im Register, und kein Charakter mit dem gedruckten Namen existiert |
| `serial_mismatch` | Nicht im Register, aber ein Charakter mit dem gedruckten Namen existiert |
| `lost`, `stolen`, `seized`, `suspended`, `replaced`, `revoked` | Der Status des Dokuments |
| `expired` | Das Ablaufdatum ist überschritten |
| `license_missing` | Der Besitzer hat die Lizenz (oder keine ihrer Klassen) nicht mehr |
| `class_revoked:<class>` | Eine auf der Karte gedruckte Klasse ist nicht mehr vorhanden, zum Beispiel `class_revoked:C` |
| `left_job` | Der Besitzer des Dienstausweises hat den Job nicht mehr |
| `data_mismatch` | Der gedruckte Name oder das Geburtsdatum weicht vom Register ab |
