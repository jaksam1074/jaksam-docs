---
title: "Replace Stash/Safe/Armory"
description: "Use your own stash, safe, or armory system instead of the default one by creating a stash module."
icon: "box"
---

## How to replace it

<Steps>
  <Step title="Navigate to the modules folder">
    Go to the `jobs_creator/_modules` folder.
  </Step>
  <Step title="Find the stash module type">
    Look for the existing **stash**-type module to use as a template.
  </Step>
  <Step title="Duplicate the module">
    Copy the existing stash module and paste it in the same folder.
  </Step>
  <Step title="Rename the copy">
    Rename the pasted copy to match your integration (e.g. `my_stash.lua`).
  </Step>
  <Step title="Open the file">
    Open the newly renamed file.
  </Step>
  <Step title="Modify the events">
    Edit the file's content so it calls the events/exports of your own stash, safe, or armory script instead of the default ones.
  </Step>
  <Step title="Select the module in-game">
    Open the `/jobscreator` menu, go to settings, and choose your new module for the job.
  </Step>
</Steps>

<Note>
  For more details on how modules work in general, see the [Modules](https://jaksam.mintlify.site/jobs-creator/modules) page.
</Note>