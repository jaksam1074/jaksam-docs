---
title: "Standard-Event-Namen ersetzen"
description: "Benenne die externen Event-Namen um, die Jobs Creator auslöst, um sie an die Scripts deines eigenen Servers anzupassen."
icon: "pen"
hidden: true
---

# Standard-Event-Namen ersetzen

Falls dein Server andere Event-Namen als die Standardnamen verwendet, kannst du diese Namen in `jobs_creator/integrations/cl_integrations.lua` **und** `jobs_creator/integrations/sv_integrations.lua` bearbeiten

Beispiel der Standardnamen:

```lua
EXTERNAL_EVENTS_NAMES = {
    ["esx:getSharedObject"] = nil,
    
    ["esx_skin:save"] = "esx_skin:save",

    ["esx_billing:sendBill"] = "esx_billing:sendBill",

    ["jsfour-idcard:open"] = "jsfour-idcard:open",

    ["esx_license:removeLicense"] = "esx_license:removeLicense",
    ["esx_license:addLicense"] = "esx_license:addLicense",
}
```

<br />Beispiel der bearbeiteten Namen:

```lua
EXTERNAL_EVENTS_NAMES = {
    ["esx:getSharedObject"] = "gamemode:getSharedObject",
    
    ["esx_skin:save"] = "my_skin_script:save",

    ["esx_billing:sendBill"] = "billing_ui:sendBill",

    ["jsfour-idcard:open"] = "jsfour-idcard:open",

    ["esx_license:removeLicense"] = "licenses:removeLicense",
    ["esx_license:addLicense"] = "licenses:addLicense",
}
```
