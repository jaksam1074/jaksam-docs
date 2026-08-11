---
title: "Territorien"
description: "Polygon-basierte Zonen, die von Gangs oder Jobs besessen und umkämpft werden können."
icon: "map"
---

Territorien sind polygon-basierte Zonen, die von Gangs oder Jobs besessen und umkämpft werden können. Die Fraktion mit den meisten Punkten oberhalb der konfigurierten Schwelle wird zum Besitzer des Territoriums.

Fraktionen können Punkte sammeln durch:

- **Drogenverkäufe** innerhalb des Territoriums (alle Verkaufsmethoden)
- **Kills** (optional, über das Ingame-Menü konfigurierbar)
- **Externe Scripts** über den [giveTerritoryPoints](/de/drugs-creator/server/territories/give-territory-points)-Export

Der Besitz eines Territoriums bietet Vorteile wie höhere Verkaufspreise für Drogen, geringere Wahrscheinlichkeit eines Polizei-Alarms und Zugriff auf das [Angeheuerte-Dealer](/de/drugs-creator/server/hired-dealers)-System.

Das System unterstützt außerdem **Hot Zones** — zufällig ausgewählte Territorien, die vorübergehende Bonus-Multiplikatoren erhalten — und **Punkte-Verfall** über konfigurierbare Intervalle.

Die gesamte Territoriums-Konfiguration (Zonen, Schwellenwerte, Fraktionen, Hot Zones, Verfall) wird über das Ingame-Menü `/drugscreator` verwaltet.

<CardGroup cols={2}>
  <Card title="Territoriums-Punkte geben" icon="arrow-up" href="/de/drugs-creator/server/territories/give-territory-points">
    Füge einer Fraktion Punkte in einem Territorium hinzu.
  </Card>

  <Card title="Territoriums-Punkte entfernen" icon="arrow-down" href="/de/drugs-creator/server/territories/remove-territory-points">
    Entferne die Punkte einer Fraktion in einem Territorium.
  </Card>

  <Card title="Territoriums-Punkte zurücksetzen" icon="rotate-left" href="/de/drugs-creator/server/territories/reset-territory-points">
    Setze die Punkte einer Fraktion in einem Territorium auf 0 zurück.
  </Card>

  <Card title="Besitzer geändert" icon="flag" href="/de/drugs-creator/server/territories/ownership-changed">
    Wird ausgelöst, wenn ein Territorium den Besitzer wechselt.
  </Card>
</CardGroup>
