---
title: "Society-Kontogeld hinzufügen"
description: "Füge dem Society-Konto eines Jobs Geld hinzu."
icon: "sack-dollar"
---

Fügt einer Society Geld hinzu.

<CodeGroup>

```lua Export
exports["jobs_creator"]:addSocietyMoney(jobName, amount)
```

```lua Beispiel
local isSuccessful = exports["jobs_creator"]:addSocietyMoney("police", 5000)
print(isSuccessful)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `jobName` | string | Job-ID (Beispiel: police) |
| `amount` | integer | Hinzuzufügender Geldbetrag |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isSuccessful` | boolean | Ob das Geld hinzugefügt wurde oder nicht |
