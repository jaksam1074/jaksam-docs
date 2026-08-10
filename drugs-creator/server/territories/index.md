---
title: "Territories"
description: "Polygon-based zones that can be owned and contested by gangs or jobs."
icon: "map"
---

Territories are polygon-based zones that can be owned and contested by gangs or jobs. The faction with the most points above the configured threshold becomes the territory owner.

Factions can earn points through:

- **Drug sales** within the territory (all selling methods)
- **Kills** (optional, configurable via the in-game menu)
- **External scripts** via the [giveTerritoryPoints](/drugs-creator/server/territories/give-territory-points) export

Territory ownership provides benefits such as higher drug sale prices, reduced police alert chances, and access to the [Hired Dealers](/drugs-creator/server/hired-dealers) system.

The system also supports **hot zones** — randomly selected territories that receive temporary bonus multipliers — and **point decay** over configurable intervals.

All territory configuration (zones, thresholds, factions, hot zones, decay) is managed through the in-game `/drugscreator` menu.

<CardGroup cols={2}>
  <Card title="Give territory points" icon="arrow-up" href="/drugs-creator/server/territories/give-territory-points">
    Add points to a faction in a territory.
  </Card>

  <Card title="Remove territory points" icon="arrow-down" href="/drugs-creator/server/territories/remove-territory-points">
    Remove points from a faction in a territory.
  </Card>

  <Card title="Reset territory points" icon="rotate-left" href="/drugs-creator/server/territories/reset-territory-points">
    Reset a faction's points in a territory to 0.
  </Card>

  <Card title="Ownership changed" icon="flag" href="/drugs-creator/server/territories/ownership-changed">
    Triggered when a territory changes owner.
  </Card>
</CardGroup>
