---
title: "Hooks"
description: "Editable server functions of Jaksam Identity: permissions, raid dispatch, admin log and phone number."
icon: "code"
---

This page lists the **server-side** hooks of Jaksam Identity. They live in `editable/server.lua` and `bridge/phone.lua`, which stay open in the escrowed release. Change the bodies, but keep the function names and arguments.

<CardGroup cols={2}>
  <Card title="Can issue" icon="user-check" href="/jaksam-identity/server/hooks/can-issue">
    Decide who may issue a real document.
  </Card>

  <Card title="Can enter workshop" icon="door-open" href="/jaksam-identity/server/hooks/can-enter-workshop">
    Add your own conditions to enter a forgery workshop.
  </Card>

  <Card title="Can raid" icon="building-shield" href="/jaksam-identity/server/hooks/can-raid">
    Add your own conditions to break a workshop door open.
  </Card>

  <Card title="On raid" icon="tower-broadcast" href="/jaksam-identity/server/hooks/on-raid">
    Send a dispatch call or your own alarm when a raid moves on.
  </Card>

  <Card title="On log" icon="clipboard-list" href="/jaksam-identity/server/hooks/on-log">
    Send every line of the admin trail to Discord or a log service.
  </Card>

  <Card title="Phone number" icon="phone" href="/jaksam-identity/server/hooks/phone-number">
    Print the number of another phone script on business cards.
  </Card>
</CardGroup>

`Editable.OnIssued` and `Editable.OnForged` receive the same arguments as the [document issued](/jaksam-identity/server/events/document-issued) and [document forged](/jaksam-identity/server/events/document-forged) events.
