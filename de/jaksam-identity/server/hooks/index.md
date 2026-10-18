---
title: "Hooks"
description: "Editierbare Server-Funktionen von Jaksam Identity: Berechtigungen, Razzia-Dispatch, Admin-Log und Telefonnummer."
icon: "code"
---

Diese Seite listet die **server-seitigen** Hooks von Jaksam Identity. Sie liegen in `editable/server.lua` und `bridge/phone.lua`, die im verschlüsselten Release offen bleiben. Ändere den Inhalt, aber behalte die Funktionsnamen und Argumente.

<CardGroup cols={2}>
  <Card title="Darf ausstellen" icon="user-check" href="/de/jaksam-identity/server/hooks/can-issue">
    Entscheiden, wer ein echtes Dokument ausstellen darf.
  </Card>

  <Card title="Darf Werkstatt betreten" icon="door-open" href="/de/jaksam-identity/server/hooks/can-enter-workshop">
    Eigene Bedingungen zum Betreten einer Fälscherwerkstatt hinzufügen.
  </Card>

  <Card title="Darf stürmen" icon="building-shield" href="/de/jaksam-identity/server/hooks/can-raid">
    Eigene Bedingungen zum Aufbrechen einer Werkstatttür hinzufügen.
  </Card>

  <Card title="Bei Razzia" icon="tower-broadcast" href="/de/jaksam-identity/server/hooks/on-raid">
    Einen Dispatch-Ruf oder deinen eigenen Alarm senden, wenn eine Razzia weitergeht.
  </Card>

  <Card title="Bei Log" icon="clipboard-list" href="/de/jaksam-identity/server/hooks/on-log">
    Jede Zeile des Admin-Protokolls an Discord oder einen Log-Dienst senden.
  </Card>

  <Card title="Telefonnummer" icon="phone" href="/de/jaksam-identity/server/hooks/phone-number">
    Die Nummer eines anderen Handy-Scripts auf Visitenkarten drucken.
  </Card>
</CardGroup>

`Editable.OnIssued` und `Editable.OnForged` bekommen dieselben Argumente wie die Events [Dokument ausgestellt](/de/jaksam-identity/server/events/document-issued) und [Dokument gefälscht](/de/jaksam-identity/server/events/document-forged).
