---
title: "Society-Kontogeld entfernen"
description: "Entferne Geld vom Society-Konto eines Jobs."
icon: "sack-dollar"
---

Entfernt Geld von einer Society.

<CodeGroup>

```lua Export
exports["jobs_creator"]:removeSocietyMoney(jobName, amount)
```

```lua Beispiel
local isSuccessful = exports["jobs_creator"]:removeSocietyMoney("police", 5000)
print(isSuccessful)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `jobName` | string | Job-ID (Beispiel: police) |
| `amount` | integer | Zu entfernender Geldbetrag |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isSuccessful` | boolean | Ob das Geld entfernt wurde oder nicht |
