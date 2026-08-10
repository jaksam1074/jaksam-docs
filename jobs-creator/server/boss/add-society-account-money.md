---
title: "Add society account money"
description: "Add money to a job's society account."
icon: "sack-dollar"
---

Add money to a society.

<CodeGroup>

```lua Export
exports["jobs_creator"]:addSocietyMoney(jobName, amount)
```

```lua Example
local isSuccessful = exports["jobs_creator"]:addSocietyMoney("police", 5000)
print(isSuccessful)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `jobName` | string | Job ID (example: police) |
| `amount` | integer | Amount of money to add |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `isSuccessful` | boolean | Whether the money was added or not |