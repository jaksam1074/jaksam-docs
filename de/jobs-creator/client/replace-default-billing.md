---
title: "Standard-Billing ersetzen"
description: "Ersetze das Standard-Billing-Verhalten, das über das Actions-Menü ausgelöst wird."
icon: "file-invoice-dollar"
---

Wird ausgelöst, wenn die Billing-Option im F6-Actions-Menü verwendet wird.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:actions:createBilling", function()
end)
```

```lua Beispiel
-- In jobs_creator/integrations/cl_integrations.lua einfügen
RegisterNetEvent("jobs_creator:framework:ready", function()
    -- Deaktiviert das Standard-Billing des Scripts (sonst gäbe es 2 Billings)
    exports["jobs_creator"]:disableScriptEvent("jobs_creator:actions:createBilling")
end)
RegisterNetEvent("jobs_creator:actions:createBilling", function()
    -- Verwendet das Billing-UI-Event
    TriggerEvent("billing_ui:activateBillingMode")
end)
```

</CodeGroup>

### Wo füge ich den Code ein?

Du kannst ihn in die Datei `integrations/cl_integrations.lua` des Scripts einfügen, **am Ende der Datei in neuen Zeilen**.
