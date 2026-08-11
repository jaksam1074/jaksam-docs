---
title: "Server"
description: "Server-seitige Events und Exports, die in Vehicles Keys verfügbar sind."
icon: "server"
---

Diese Seite listet die **server-seitigen** Events und Exports auf, die in Vehicles Keys verfügbar sind.

<CardGroup cols={2}>
  <Card title="Schlüssel an Identifier geben" icon="key" href="/de/vehicles-keys/server/give-keys-to-identifier">
    Gib einem Spieler Fahrzeugschlüssel anhand seines Identifiers.
  </Card>

  <Card title="Schlüssel an Spieler-ID geben" icon="key" href="/de/vehicles-keys/server/give-keys-to-player-id">
    Gib einem online Spieler Fahrzeugschlüssel.
  </Card>

  <Card title="Schlüssel von Identifier entfernen" icon="key" href="/de/vehicles-keys/server/remove-keys-from-identifier">
    Entferne Fahrzeugschlüssel eines Spielers anhand seines Identifiers.
  </Card>

  <Card title="Schlüssel von Spieler-ID entfernen" icon="key" href="/de/vehicles-keys/server/remove-keys-from-player-id">
    Entferne Fahrzeugschlüssel eines online Spielers.
  </Card>

  <Card title="Identifier-Schlüssel abrufen" icon="list" href="/de/vehicles-keys/server/get-identifier-keys">
    Ruft alle Schlüssel ab, die einem Identifier gehören.
  </Card>

  <Card title="Spieler-ID-Schlüssel abrufen" icon="list" href="/de/vehicles-keys/server/get-player-id-keys">
    Ruft alle Schlüssel ab, die einem online Spieler gehören.
  </Card>

  <Card title="Prüfen, ob Spieler-ID Kennzeichen besitzt" icon="circle-question" href="/de/vehicles-keys/server/get-if-player-id-owns-a-plate">
    Prüft, ob ein Spieler ein Kennzeichen besitzt.
  </Card>

  <Card title="Eigene Fahrzeuge des Spielers aktualisieren" icon="rotate" href="/de/vehicles-keys/server/refresh-player-owned-vehicles">
    Aktualisiert die Liste der eigenen Fahrzeuge eines Spielers.
  </Card>

  <Card title="Fahrzeug ver-/entriegelt" icon="lock" href="/de/vehicles-keys/server/vehicle-locked-unlocked">
    Wird ausgelöst, wenn sich der Schließzustand eines Fahrzeugs ändert.
  </Card>

  <Card title="Fahrzeugfenster zerstört" icon="car-burst" href="/de/vehicles-keys/server/vehicle-window-broken">
    Wird ausgelöst, wenn ein Spieler ein Fahrzeugfenster zerstört.
  </Card>

  <Card title="Spieler hat Fahrzeug kurzgeschlossen" icon="bolt" href="/de/vehicles-keys/server/player-hotwired-a-vehicle">
    Wird ausgelöst, wenn ein Fahrzeug kurzgeschlossen wird.
  </Card>

  <Card title="Spieler hat Fahrzeug geknackt" icon="lock-open" href="/de/vehicles-keys/server/player-lockpicked-a-vehicle">
    Wird ausgelöst, wenn ein Fahrzeugschloss geknackt wird.
  </Card>

  <Card title="Polizei alarmiert" icon="siren-on" href="/de/vehicles-keys/server/police-alerted">
    Wird einmalig server-seitig ausgelöst, wenn die Polizei alarmiert wird.
  </Card>

  <Card title="Alarme" icon="bell" href="/de/vehicles-keys/server/alarms">
    Events für die Aktivierung von Fahrzeugalarmen.
  </Card>
</CardGroup>
