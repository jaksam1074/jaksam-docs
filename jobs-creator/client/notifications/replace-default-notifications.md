---
title: "Replace notifications"
description: "Use a custom notification system instead of the default one by creating a notify module."
icon: "bell"
---

Used to show the normal notifications, for example `"You are not on duty"`. These are the normal notifications, not TextUI, but the process is the same for both.

## How to replace it

<Steps>
  <Step title="Navigate to the modules folder">
    Go to the `jobs_creator/_modules` folder.
  </Step>
  <Step title="Find the notify module type">
    Look for the existing **notify**-type module to use as a template.
  </Step>
  <Step title="Duplicate the module">
    Copy the existing notify module and paste it in the same folder.
  </Step>
  <Step title="Rename the copy">
    Rename the pasted copy to match your integration (e.g. `my_notify.lua`).
  </Step>
  <Step title="Open the file">
    Open the newly renamed file.
  </Step>
  <Step title="Modify the events">
    Edit the file's content so it calls the events/exports of your own notification script instead of the default ones.
  </Step>
  <Step title="Select the module in-game">
    Open the `/jobscreator` menu, go to settings, and choose your new module for the job.
  </Step>
</Steps>

<Note>
  For more details on how modules work in general, see the [Modules](https://jaksam.mintlify.site/jaksam-scripts/modules) page.
</Note>