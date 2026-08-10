---
title: "Remove society account money"
description: "Remove money from a job's society account."
icon: "sack-dollar"
---

Remove money from a society.

<CodeGroup>

```lua Export
exports["jobs_creator"]:removeSocietyMoney(jobName, amount)
```

```lua Example
local isSuccessful = exports["jobs_creator"]:removeSocietyMoney("police", 5000)
print(isSuccessful)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `jobName` | string | Job ID (example: police) |
| `amount` | integer | Amount of money to remove |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `isSuccessful` | boolean | Whether the money was removed or not |