---
title: "Get job account money"
description: "Retrieve the amount of money stored in a job's society account."
icon: "sack-dollar"
---

Get the amount of money stored in a job's society account.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getJobAccountMoney(jobName)
```

```lua Example
local jobMoney = exports["jobs_creator"]:getJobAccountMoney("gang_job")
print(jobMoney)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `jobName` | string | Job ID (example: police) |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `accountMoney` | integer | Money stored in the society account |