---
title: "Replace default search action"
description: "Use a custom search action instead of the default one by creating a search module."
icon: "magnifying-glass"
---

By default, the search action uses Jobs Creator's built-in search behavior. If you want to use your own stash, safe, or armory system instead, you can replace it with a custom **module**.

## How to replace it

<Steps>
  <Step title="Navigate to the modules folder">
    Go to the `jobs_creator/_modules` folder.
  </Step>
  <Step title="Find the search module type">
    Look for the existing **search**-type module to use as a template.
  </Step>
  <Step title="Duplicate the module">
    Copy the existing search module and paste it in the same folder.
  </Step>
  <Step title="Rename the copy">
    Rename the pasted copy to match your integration (e.g. `my_stash_search.lua`).
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
  For more details on how modules work in general, see the [Modules](/jobs-creator/modules) page.
</Note>