---
title: "Check"
description: "Register check of a document serial, as an authority sees it."
icon: "magnifying-glass"
---

Returns what an authority sees when it checks a document in the register. It never reveals who made a forgery or its quality.

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `serial` | string | The document number |
| `printed` | table (optional) | What is printed on the card: `{ firstname, lastname, dob }`. Used to tell a wrong serial from a person that doesn't exist, and to spot printed data that differs from the register |

### Return value

A table:

| Name | Data Type | Description |
| --- | --- | --- |
| `found` | boolean | **true** if the serial is in the register (a real document) |
| `personExists` | boolean | Only when `found` is **false**: whether a character with the printed name exists |
| `status` | string | Only when found: `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` or `revoked`. A suspension that has ended returns `valid` |
| `problems` | table | List of strings, empty when everything is fine (see below) |
| `record` | table | Only when found: the register row (`serial`, `doc_type`, `owner`, `firstname`, `lastname`, `dob`, `sex`, `classes`, `issued_at`, `expires_at`, `status`, `status_until`, `status_note`, ...) |
| `currentClasses` | string | Only for documents with licence classes: the classes the owner holds now, for example `A, B` |

### Problems

| Problem | Meaning |
| --- | --- |
| `person_not_found` | Not in the register, and no character with the printed name exists |
| `serial_mismatch` | Not in the register, but a character with the printed name exists |
| `lost`, `stolen`, `seized`, `suspended`, `replaced`, `revoked` | The status of the document |
| `expired` | The expiry date has passed |
| `license_missing` | The owner no longer holds the licence (or any of its classes) |
| `class_revoked:<class>` | A class printed on the card is no longer held, for example `class_revoked:C` |
| `left_job` | The badge owner no longer has the job |
| `data_mismatch` | The printed name or date of birth differs from the register |
