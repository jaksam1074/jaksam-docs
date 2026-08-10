---
title: "Item removed"
description: "Hook triggered when an item is removed from an inventory."
icon: "circle-minus"
---

Triggered when an item is removed from an inventory. Register with [`registerHook`](/jaksam-inventory/hooks#register-a-hook) using the event name `onItemRemoved`.

### Payload

| Field | Data Type | Description |
| --- | --- | --- |
| `inventoryId` | string | e.g. `"player:1"` |
| `itemName` | string | e.g. `"bread"` |
| `amount` | number | Amount removed |
| `metadata` | table \| nil | Item metadata |
| `slotId` | number | Slot the item was removed from |

<Info>
  [TODO: INFORMATION NEEDED] The source material didn't include a dedicated example for this specific hook. See [Hooks overview](/jaksam-inventory/hooks) for the general `registerHook` pattern and filters, which apply the same way here.
</Info>
