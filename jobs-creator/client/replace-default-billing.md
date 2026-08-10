---
title: "Replace default billing"
description: "Replace the default billing behavior triggered from the actions menu."
icon: "file-invoice-dollar"
---

Triggered when using the billing option in the F6 actions menu.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:actions:createBilling", function()
end)
```

```lua Example
-- To place in jobs_creator/integrations/cl_integrations.lua
RegisterNetEvent("jobs_creator:framework:ready", function()
    -- Disables the default script billing (otherwise there would be 2 billings)
    exports["jobs_creator"]:disableScriptEvent("jobs_creator:actions:createBilling")
end)
RegisterNetEvent("jobs_creator:actions:createBilling", function()
    -- Uses Billing UI event
    TriggerEvent("billing_ui:activateBillingMode")
end)
```

</CodeGroup>

### Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**.