---
title: "QBCore jobs injection"
description: "Fix other scripts not recognizing Jobs Creator jobs on QBCore due to script start order."
icon: "plug"
---

Usually you are not required to add any code. Despite this, different script start orders may cause other scripts to not recognize Jobs Creator jobs on QBCore.

## How can I fix this?

The solution is very easy — add the following event client side and server side in the script that isn't recognizing the Jobs Creator jobs:

```lua
-- jaksam's Jobs Creator integration
AddEventHandler('jobs_creator:injectJobs', function(jobs)
    -- Assign the new jobs to the QBCore object, the following line depends on how your script is structured
    QBCore.Shared.Jobs = jobs
end)
```
