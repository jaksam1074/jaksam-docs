---
title: "Job-Kontogeld abrufen"
description: "Rufe den Geldbetrag ab, der im Society-Konto eines Jobs gespeichert ist."
icon: "sack-dollar"
---

Ruft den Geldbetrag ab, der im Society-Konto eines Jobs gespeichert ist.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getJobAccountMoney(jobName)
```

```lua Beispiel
local jobMoney = exports["jobs_creator"]:getJobAccountMoney("gang_job")
print(jobMoney)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `jobName` | string | Job-ID (Beispiel: police) |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `accountMoney` | integer | Im Society-Konto gespeichertes Geld |
