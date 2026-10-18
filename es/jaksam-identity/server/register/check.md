---
title: "Check"
description: "Consulta del registro de un número de documento, como la ve una autoridad."
icon: "magnifying-glass"
---

Devuelve lo que ve una autoridad cuando consulta un documento en el registro. Nunca revela quién hizo una falsificación ni su calidad.

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

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `serial` | string | El número del documento |
| `printed` | table (opcional) | Lo que está impreso en la tarjeta: `{ firstname, lastname, dob }`. Sirve para distinguir un número equivocado de una persona que no existe, y para detectar datos impresos que no coinciden con el registro |

### Valor de retorno

Una tabla:

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `found` | boolean | **true** si el número está en el registro (un documento real) |
| `personExists` | boolean | Solo cuando `found` es **false**: si existe un personaje con el nombre impreso |
| `status` | string | Solo si se encuentra: `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` o `revoked`. Una suspensión terminada devuelve `valid` |
| `problems` | table | Lista de strings, vacía si todo está bien (mira abajo) |
| `record` | table | Solo si se encuentra: la fila del registro (`serial`, `doc_type`, `owner`, `firstname`, `lastname`, `dob`, `sex`, `classes`, `issued_at`, `expires_at`, `status`, `status_until`, `status_note`, ...) |
| `currentClasses` | string | Solo para documentos con clases de licencia: las clases que tiene ahora el dueño, por ejemplo `A, B` |

### Problemas

| Problema | Significado |
| --- | --- |
| `person_not_found` | No está en el registro, y no existe ningún personaje con el nombre impreso |
| `serial_mismatch` | No está en el registro, pero existe un personaje con el nombre impreso |
| `lost`, `stolen`, `seized`, `suspended`, `replaced`, `revoked` | El estado del documento |
| `expired` | La fecha de caducidad ha pasado |
| `license_missing` | El dueño ya no tiene la licencia (ni ninguna de sus clases) |
| `class_revoked:<class>` | Una clase impresa en la tarjeta ya no se tiene, por ejemplo `class_revoked:C` |
| `left_job` | El dueño de la placa ya no tiene el trabajo |
| `data_mismatch` | El nombre o la fecha de nacimiento impresos no coinciden con el registro |
