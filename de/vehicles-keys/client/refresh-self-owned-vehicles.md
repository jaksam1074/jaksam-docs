---
title: "Eigene Fahrzeuge aktualisieren"
description: "Aktualisiert die Liste der eigenen Fahrzeuge des lokalen Spielers client-seitig, z.B. nach dem Kauf eines neuen Fahrzeugs."
icon: "rotate"
---

Das Auslösen dieses Events (client-seitig) aktualisiert die Liste der Fahrzeuge des Spielers (aus `owned_vehicles` bei ESX oder `player_vehicles` bei QBCore).

Dies ist nützlich, um die Liste der eigenen Fahrzeuge zu aktualisieren, wenn ein Spieler ein neues Fahrzeug kauft — du kannst diese Codezeile direkt nach einem erfolgreichen Fahrzeugkauf hinzufügen.

```lua Event
TriggerServerEvent("vehicles_keys:refreshMineOwnedVehicles")
```
