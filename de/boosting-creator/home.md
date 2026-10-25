---
title: "Boosting Creator"
description: "Offizielle Dokumentation für das FiveM-Script Boosting Creator: Boosting-Aufträge nach Klasse, GPS-Tracker, Wachen, Gang-Verfolgungen, Fixer, Garagen und Autotransporter."
icon: "car-burst"
---

Dies ist die offizielle Dokumentation von **Boosting Creator**.

Boosting Creator macht Autodiebstahl zu einem kompletten Job. Spieler öffnen einen Laptop, stellen sich in die Warteschlange und bekommen Aufträge nach Klasse: das geparkte Auto finden, aufbrechen und kurzschließen, einen GPS-Tracker und eine bewaffnete Gang abschütteln und es dann einem Käufer übergeben, die VIN abschleifen, um es zu behalten, es in einem Chop Shop ausschlachten oder es in der eigenen Garage abstellen, um es später zu verkaufen. Alles wird im Spiel über ein einziges Admin-Panel eingerichtet, ohne Neustart.

<CardGroup cols={2}>
  <Card title="Store" icon="cart-shopping" href="https://fivem.jaksam-scripts.com/">
    Kaufe oder sieh dir das Script im jaksam Store an.
  </Card>

  <Card title="Showcase" icon="play" href="https://youtu.be/5A-XnFG2Pw0">
    Sieh dir den kompletten Showcase auf YouTube an.
  </Card>

  <Card title="Unterstützte Sprachen" icon="language">
    Englisch, Deutsch, Spanisch, Französisch, Italienisch
  </Card>
</CardGroup>

## Was es macht

<CardGroup cols={2}>
  <Card title="Aufträge nach Klasse" icon="ranking-star">
    Klassen von D bis S, mit Ruf freigeschaltet, jede mit eigenen Fahrzeugen, Bezahlung, Zeitlimit, Mindestanzahl Polizei und Risiken.
  </Card>

  <Card title="Diebstahl und Tracker" icon="satellite-dish">
    Aufbrechen, mit einem Minispiel kurzschließen und dann den GPS-Tracker hacken, während die Polizei seinen Pings folgt.
  </Card>

  <Card title="Wachen und Gang-Verfolgung" icon="user-ninja">
    Bewaffnete Wachen um das Auto und Verfolgerautos mit Schützen, sobald es gestohlen ist.
  </Card>

  <Card title="Fixer" icon="envelope">
    Käufer mit Namen, die per E-Mail schreiben, ein Auto ohne Kratzer, eine Umlackierung oder Tuning verlangen und dem Dieb mit jedem Job mehr vertrauen.
  </Card>

  <Card title="Crews" icon="users">
    Bis zu 4 Spieler teilen sich einen Auftrag, mit aufgeteilter Bezahlung und einem Bonus für die Crew.
  </Card>

  <Card title="Garagen und Autotransporter" icon="warehouse">
    Gestohlene Autos in einer Garage für 6 Autos abstellen und einzeln oder alle zusammen auf einem Autotransporter verkaufen.
  </Card>
</CardGroup>

## Dokumentation

<CardGroup cols={2}>
  <Card title="Installation" icon="download" href="/de/boosting-creator/installation">
    Boosting Creator auf deinem Server installieren und zum Laufen bringen.
  </Card>

  <Card title="Anleitungen" icon="book-open" href="/de/boosting-creator/guides/how-it-works">
    Wie ein Auftrag abläuft, Klassen, Orte, Fixer, Crews, Garagen und Polizei.
  </Card>

  <Card title="FAQ" icon="circle-question" href="/de/boosting-creator/faq">
    Häufig gestellte Fragen.
  </Card>

  <Card title="Entwickler-Referenz" icon="code" href="/de/boosting-creator/editable-files">
    Editierbare Dateien, Hooks und Exports für Entwickler.
  </Card>
</CardGroup>

## Framework-Unterstützung

<CardGroup cols={3}>
  <Card title="ESX" icon="code" href="/de/boosting-creator/installation">
    Bezahlung auf jedes Konto, Autos mit abgeschliffener VIN werden in `owned_vehicles` gespeichert.
  </Card>

  <Card title="QBCore" icon="code" href="/de/boosting-creator/installation">
    Autos mit abgeschliffener VIN werden in `player_vehicles` gespeichert, Society-Bezahlung über qb-banking oder qb-management.
  </Card>

  <Card title="Qbox" icon="code" href="/de/boosting-creator/installation">
    Funktioniert mit qbx_core über die QBCore-Version.
  </Card>
</CardGroup>
