---
title: "How to edit minigames"
description: "Add your own custom minigame to Robberies Creator."
icon: "gamepad"
---

You can add any minigame you want — doing so will require a minimum of coding knowledge on your side.

<Steps>
  <Step title="Create your minigame file">
    Add your minigame file in `integrations/minigames` and create your function (using `datacrack.lua`, or any other existing minigame, as an example).
  </Step>
  <Step title="Register the minigame">
    Edit the file `integrations/cl_hack_minigame.lua` to support your minigame.
  </Step>
  <Step title="Add it to the UI">
    Edit `html/index.js`, search for `"datacrack"`, and add your minigame there as well.
  </Step>
</Steps>
