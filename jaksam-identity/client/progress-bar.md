---
title: "Progress bar"
description: "Replace the progress bar used for breaching a door, seizing evidence and shredding."
icon: "spinner"
---

Everything that takes time and can be given up (breaking a door open, seizing, shredding) runs through one function. By default it is `lib.progressBar` from ox_lib.

Edit `Editable.Progress` in `editable/client.lua`:

<CodeGroup>

```lua Function
function Editable.Progress(seconds, label)
    return lib.progressBar({
        duration = seconds * 1000, label = label, useWhileDead = false, canCancel = true,
        disable = { move = true, car = true, combat = true },
        anim = { dict = 'mini@repair', clip = 'fixing_a_player' },
    }) == true
end
```

```lua Example
function Editable.Progress(seconds, label)
    return exports['my_progressbar']:Start({
        time = seconds * 1000,
        text = label,
        cancelable = true,
    })
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `seconds` | number | How long the action takes |
| `label` | string | The text to show with the progress bar |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `completed` | boolean | **true** when it ran to the end, **false** when the player cancelled it |
