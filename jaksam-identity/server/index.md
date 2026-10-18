---
title: "Server"
description: "Server-side exports, events and hooks available in Jaksam Identity."
icon: "server"
---

This page lists the **server-side** exports, events and hooks available in Jaksam Identity, for MDT, DMV, phone and job scripts.

<CardGroup cols={2}>
  <Card title="Register" icon="address-book" href="/jaksam-identity/server/register">
    Check, issue and change the status of real documents.
  </Card>

  <Card title="Wallet" icon="wallet" href="/jaksam-identity/server/wallet">
    Read the documents a player carries and show one, for phone scripts.
  </Card>

  <Card title="Events" icon="bolt" href="/jaksam-identity/server/events">
    Triggered when a document is issued, forged or changes status.
  </Card>

  <Card title="Hooks" icon="code" href="/jaksam-identity/server/hooks">
    Editable functions in `editable/server.lua` and `bridge/phone.lua`.
  </Card>
</CardGroup>

<Note>
  The register only holds **real** documents. A forged document never appears in it: a register check of a forged serial returns "no record", exactly as the police would see it.
</Note>
