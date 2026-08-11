---
title: "Panik-Knopf manuell starten"
description: "Löse den Panik-Knopf aus deinem eigenen Code aus, ohne dass der Hotkey benötigt wird."
icon: "hand-pointer"
---

Du kannst dieses Event nutzen, um den Panik-Knopf manuell zu starten, ohne dass der Spieler überhaupt den Hotkey drücken muss — zum Beispiel aus einem Radial-Menü heraus.

<Note>
  Der Hotkey für den Panik-Knopf kann in den Menü-Einstellungen deaktiviert werden.
</Note>

```lua Event
TriggerServerEvent("trackers_creator:panicButtonPressed")
```
