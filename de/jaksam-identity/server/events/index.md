---
title: "Events"
description: "Server-Events, die Jaksam Identity auslöst, wenn ein Dokument ausgestellt, gefälscht wird oder seinen Status ändert."
icon: "bolt"
---

Diese Seite listet die **server-seitigen** Events, die Jaksam Identity auslöst. Es sind lokale Server-Events: Höre sie mit `AddEventHandler` in einem anderen Server-Script ab.

<CardGroup cols={2}>
  <Card title="Dokument ausgestellt" icon="id-card" href="/de/jaksam-identity/server/events/document-issued">
    Ausgelöst, nachdem ein echtes Dokument ausgestellt wurde.
  </Card>

  <Card title="Dokument gefälscht" icon="print" href="/de/jaksam-identity/server/events/document-forged">
    Ausgelöst, nachdem eine Fälschung gemacht wurde.
  </Card>

  <Card title="Status geändert" icon="tag" href="/de/jaksam-identity/server/events/status-changed">
    Ausgelöst, nachdem sich der Register-Status eines Dokuments geändert hat.
  </Card>
</CardGroup>
