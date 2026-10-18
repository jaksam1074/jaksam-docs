---
title: "Events"
description: "Server events triggered by Jaksam Identity when a document is issued, forged or changes status."
icon: "bolt"
---

This page lists the **server-side** events triggered by Jaksam Identity. They are local server events: listen to them with `AddEventHandler` in another server script.

<CardGroup cols={2}>
  <Card title="Document issued" icon="id-card" href="/jaksam-identity/server/events/document-issued">
    Triggered after a real document is issued.
  </Card>

  <Card title="Document forged" icon="print" href="/jaksam-identity/server/events/document-forged">
    Triggered after a forgery is made.
  </Card>

  <Card title="Status changed" icon="tag" href="/jaksam-identity/server/events/status-changed">
    Triggered after the register status of a document changes.
  </Card>
</CardGroup>
