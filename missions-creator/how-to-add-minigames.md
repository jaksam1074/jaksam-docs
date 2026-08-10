---
title: "How to add minigames"
description: "Add your own custom minigame to Missions Creator."
icon: "gamepad"
---

Adding new minigames is easy. Follow this procedure to add a new minigame:

<Steps>
  <Step title="Duplicate the example file">
    Duplicate the file `missions_creator/client/minigames/_EXAMPLE_MINIGAME.lua`.
  </Step>
  <Step title="Rename the file">
    Rename the file to your minigame's name.
  </Step>
  <Step title="Remove the comment markers">
    Open the new file and remove the comments at the beginning and at the end of the file (remove the `--[[` and `--]]` symbols).
  </Step>
  <Step title="Rename the minigame">
    Change `YOUR_MINIGAME_NAME` to your minigame's name.
  </Step>
  <Step title="Implement your minigame">
    Edit the function to support your minigame. It must return `true` on success and `false` on failure. You can see examples in `datacrack.lua`, `fingerprint.lua`, and `memory_game.lua`.
  </Step>
  <Step title="Restart the script">
    Save the file and restart the script. If everything was done correctly (especially implementing the minigame itself), you should see your minigame in the script's list of minigames.
  </Step>
</Steps>
