---
title: "Server"
description: "Server-seitige Exports, Events und Hooks in Jaksam Identity."
icon: "server"
---

Diese Seite listet die **server-seitigen** Exports, Events und Hooks von Jaksam Identity, für MDT-, DMV-, Handy- und Job-Scripts.

<CardGroup cols={2}>
  <Card title="Register" icon="address-book" href="/de/jaksam-identity/server/register">
    Echte Dokumente prüfen, ausstellen und ihren Status ändern.
  </Card>

  <Card title="Wallet" icon="wallet" href="/de/jaksam-identity/server/wallet">
    Die Dokumente lesen, die ein Spieler trägt, und eines zeigen, für Handy-Scripts.
  </Card>

  <Card title="Events" icon="bolt" href="/de/jaksam-identity/server/events">
    Ausgelöst, wenn ein Dokument ausgestellt, gefälscht wird oder seinen Status ändert.
  </Card>

  <Card title="Hooks" icon="code" href="/de/jaksam-identity/server/hooks">
    Editierbare Funktionen in `editable/server.lua` und `bridge/phone.lua`.
  </Card>
</CardGroup>

<Note>
  Das Register enthält nur **echte** Dokumente. Ein gefälschtes Dokument erscheint nie darin: Eine Registerabfrage einer gefälschten Nummer liefert "kein Eintrag", genau wie die Polizei es sehen würde.
</Note>
