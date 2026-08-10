---
title: "Modules"
description: "Replace default features like notify, progress bar, stash, and logs with your own custom modules."
icon: "puzzle-piece"
---

Modules are an easy way for Jobs Creator to replace certain default features (notify, progress bar, stash, logs).

To choose an existing module, open the `/jobscreator` menu, go to settings, and choose it. As easy as that.

### How to create a custom module?

Creating a module is extremely easy:

<Steps>
  <Step title="Navigate to the modules folder">
    Go to the `jobs_creator/_modules` folder.
  </Step>
  <Step title="Choose the module type">
    Pick the module type you want to create (logs, progressbar, stash, etc.).
  </Step>
  <Step title="Duplicate an existing module">
    Copy an existing module and paste it in the same folder as a template.
  </Step>
  <Step title="Rename the copy">
    Rename the pasted copy to match the integration you want to create.
  </Step>
  <Step title="Open the file">
    Open the newly renamed file.
  </Step>
  <Step title="Modify the events">
    Edit the file's content to match the events of the third-party script you're integrating.
  </Step>
</Steps>