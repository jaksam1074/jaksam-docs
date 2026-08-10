---
title: "Replace help notification/TextUI"
description: "Use a custom TextUI system instead of the default one by creating a notify module."
icon: "message"
---

Used to show the usual `Press E to ...` prompt at the top left of the player's screen.

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
    Rename the pasted copy to match your integration (e.g. `my_textui.lua`).
  </Step>
  <Step title="Open the file">
    Open the newly renamed file.
  </Step>
  <Step title="Modify the events">
    Edit the file's content so it calls the events/exports of your own TextUI script instead of the default one.
  </Step>
  <Step title="Select the module in-game">
    Open the `/jobscreator` menu, go to settings, and choose your new module for the job.
  </Step>
</Steps>

<Note>
  For more details on how modules work in general, see the [Modules](/jobs-creator/modules) page.
</Note>