---
title: "Standardnamen ersetzen"
description: "Passe die Script-, Event- und Export-Namen an, die Jobs Creator verwendet, um sie an dein Server-Setup anzupassen."
icon: "pen-to-square"
---

## Standard-Script-Namen ersetzen

Falls dein Server andere Script-Namen als die Standardnamen verwendet, kannst du diese Namen direkt in den Einstellungen des Ingame-Menüs bearbeiten. Das ist perfekt, wenn du ein Script aus irgendeinem Grund umbenennst und dessen Exports unverändert bleiben.

<Note>
  Das ausgewählte Script muss den gleichen Export verwenden, damit es korrekt funktioniert.
</Note>

## Standard-Event-Namen ersetzen

Falls dein Server andere Event-Namen als die Standardnamen verwendet, kannst du diese Namen in `jobs_creator/integrations/cl_integrations.lua` **und** `jobs_creator/integrations/sv_integrations.lua` bearbeiten.

**Beispiel der Standardnamen:**

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

**Beispiel der bearbeiteten Namen:**

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
