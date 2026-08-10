---
title: "Pay a bill"
description: "Pay a bill by its ID, for example from an external script."
icon: "credit-card"
---

Trigger to properly pay a bill by its ID — you can use this from external scripts.

```lua Event
TriggerServerEvent("billing_ui:payInvoice", billId)
```

### Parameters

| Name     | Data Type | Description                                                  |
| -------- | --------- | ------------------------------------------------------------- |
| `billId` | integer   | The bill ID (from the database table `billing`)                 |
