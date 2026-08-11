---
title: "Shared"
icon: "circle-share-nodes"
description: "Exports, die sowohl server- als auch client-seitig funktionieren"
---

## Kompatibilität

Dieses Script funktioniert mit anderen beliebten Inventarsystemen wie es_extended, qb-inventory und ox_inventory.

<Info>
  Für ESX- und QBCore-Funktionen erfolgt die Einrichtung automatisch. Willst du aber weiterhin Exports von ox_inventory oder qb-inventory für Kompatibilität nutzen, musst du diese Option in der Datei `jaksam_inventory/integrations/sv_integrations.lua` aktivieren.
</Info>

## Shared-Funktionen

| Funktion | Beschreibung |
| --- | --- |
| [Get static items list](/de/jaksam-inventory/functions/shared/get-static-items-list) | Gibt die Liste aller Items im Inventar zurück |
| [Get static item](/de/jaksam-inventory/functions/shared/get-static-item) | Ruft allgemeine Item-Informationen ab (Gewicht, Stapelbarkeit, Beschreibung usw.) |
| [Get item label](/de/jaksam-inventory/functions/shared/get-item-label) | Ruft nur das Label (den Anzeigenamen) eines Items ab |
| [Get item image path](/de/jaksam-inventory/functions/shared/get-item-image-path) | Ruft den NUI-Bildpfad für ein Item ab |
