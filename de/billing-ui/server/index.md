---
title: "Server"
description: "Server-seitige Events und Exports, die in Billing UI verfügbar sind."
icon: "server"
---

Diese Seite listet die **server-seitigen** Events und Exports auf, die in Billing UI verfügbar sind.

<CardGroup cols={2}>
  <Card title="Rechnung erstellen" icon="file-circle-plus" href="/de/billing-ui/server/create-bill">
    Erstelle eine neue Rechnung für einen Spieler oder eine Society.
  </Card>

  <Card title="Rechnung löschen" icon="trash" href="/de/billing-ui/server/delete-bill">
    Lösche eine Rechnung anhand ihrer ID.
  </Card>

  <Card title="Rechnung aktualisieren" icon="rotate" href="/de/billing-ui/server/refresh-bill">
    Aktualisiere eine Rechnung, nachdem du sie direkt in der Datenbank bearbeitet hast.
  </Card>

  <Card title="Rechnung erstellt" icon="file-invoice" href="/de/billing-ui/server/on-bill-created">
    Wird ausgelöst, wenn eine Rechnung erstellt wird.
  </Card>

  <Card title="Rechnung bezahlt" icon="circle-check" href="/de/billing-ui/server/on-bill-paid">
    Wird ausgelöst, wenn eine Rechnung bezahlt wird.
  </Card>
</CardGroup>
