---
title: "Replacing default names"
description: "Customize the script, event, and export names Jobs Creator uses to match your server's setup."
icon: "pen-to-square"
---

## Replacing default script names

In case your server uses different script names than the default ones, you can edit those names directly in the in-game menu settings. This is perfect when you rename a script for any reason, and its exports are untouched.

<Note>
  The script you select must use the same export in order to work properly.
</Note>

## Replacing default event names

In case your server uses different event names than the default ones, you can edit those names in `jobs_creator/integrations/cl_integrations.lua` **and** `jobs_creator/integrations/sv_integrations.lua`.

**Example of default names:**

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

**Example of edited names:**

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