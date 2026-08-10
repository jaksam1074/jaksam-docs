---
title: "Progress bar"
description: "Replace the default progress bar with your own, or use the built-in one in external scripts."
icon: "spinner"
---

## How to replace it

You can use Jobs Creator [modules](https://jaksam.mintlify.site/jaksam-scripts/modules) if you want to use your own progress bar.

<Steps>
  <Step title="Navigate to the modules folder">
    Go to the `jobs_creator/_modules` folder.
  </Step>
  <Step title="Find the progressbar module type">
    Look for the existing **progressbar**-type module to use as a template.
  </Step>
  <Step title="Duplicate the module">
    Copy the existing progressbar module and paste it in the same folder.
  </Step>
  <Step title="Rename the copy">
    Rename the pasted copy to match your integration (e.g. `my_progressbar.lua`).
  </Step>
  <Step title="Open the file">
    Open the newly renamed file.
  </Step>
  <Step title="Modify the events">
    Edit the file's content so it calls the events/exports of your own progress bar script instead of the default one.
  </Step>
  <Step title="Select the module in-game">
    Open the `/jobscreator` menu, go to settings, and choose your new module for the job.
  </Step>
</Steps>

## Use in external scripts

If you like the default progress bar of the script and want to use it in external scripts, this is the event:

<CodeGroup>

```lua Event
TriggerEvent("jobs_creator:startProgressBar", timeInMS, text, hexColor)
```

```lua Example
-- This will create a command to show a red progressbar
-- /progressbar 5000 Hello
RegisterCommand("progressbar", function(playerId, args)
    TriggerEvent("jobs_creator:startProgressBar", tonumber(args[1]), args[2], "#ff0000")
end)
```

</CodeGroup>

### Parameters

| Name | Data type | Description |
| --- | --- | --- |
| `timeInMS` | integer | Duration of the progress bar in milliseconds |
| `text` | string | The text that will be shown with the progress bar |
| `hexColor` | string | The color of the progress bar in hex code (example `#70f2b4`). Can be `nil` to use the default one of the script |