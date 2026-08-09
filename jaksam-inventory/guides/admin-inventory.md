---
title: "Admin Inventory (Omnipack)"
description: "Access and manage the admin omnipack, and set up omnipack-only permissions"
icon: "warehouse"
---

If you already have admin permissions (you can see it by typing `/inventory` in-game), you can open the omnipack by simply opening your inventory (F2), and then pressing F1.

<Warning>
  Moving an item **TO** omnipack will **delete** it.
</Warning>

<Frame>
  ![Omnipack screenshot](/images/omnipack-screenshot.png)
</Frame>

## Omnipack-only access

If you want to give access **only** to the omnipack without granting access to the admin menu and commands, use the specific permission:

```bash
add_ace identifier.license:26240584e4v4ca31b22d247b8be6921a8d22j6m1 jaksam_inventory.omnipack allow # Allows only omnipack permission
```

With this permission, the player will be able to:

<CardGroup cols={2}>
  <Card title="Can do" icon="check">
    Use the omnipack (F1 in inventory)
  </Card>

  <Card title="Cannot do" icon="xmark">
    Open the admin menu (`/inventory`)

    Use admin commands (`/giveitem`, `/removeitem`, etc.)
  </Card>
</CardGroup>