---
title: "Vehicle repaired"
description: "Triggered after a vehicle is repaired via the job actions menu, useful for adding extra repair logic."
icon: "wrench"
---

Triggered after a vehicle is repaired with the job actions menu. Useful if you want to add an extra repair function to the current ones.

```lua Event
AddEventHandler("jobs_creator:vehicleRepaired", function(vehicle)
    -- You can add the extra repair functions here
end)
```

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `vehicle` | vehicle handle | The vehicle's handle |