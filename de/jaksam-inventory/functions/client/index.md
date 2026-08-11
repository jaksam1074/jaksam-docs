---
title: "Client"
icon: "laptop"
description: "Client-seitige Exports zum Lesen und Steuern des Inventars"
---

## Kompatibilität

Dieses Script funktioniert mit anderen beliebten Inventarsystemen wie es_extended, qb-inventory und ox_inventory.

<Info>
  Für ESX- und QBCore-Funktionen erfolgt die Einrichtung automatisch. Willst du aber weiterhin Exports von ox_inventory oder qb-inventory für Kompatibilität nutzen, musst du diese Option in der Datei `jaksam_inventory/integrations/sv_integrations.lua` aktivieren.
</Info>

## Client-Funktionen

| Funktion | Beschreibung |
| --- | --- |
| [Get total item amount](/de/jaksam-inventory/functions/client/get-total-item-amount) | Ermittelt die Gesamtmenge eines bestimmten Items im Inventar des Spielers |
| [Open inventory](/de/jaksam-inventory/functions/client/open-inventory) | Öffnet ein Inventar neben dem Inventar des Spielers |
| [Close inventory](/de/jaksam-inventory/functions/client/close-inventory) | Schließt die Inventar-UI |
| [Get inventory](/de/jaksam-inventory/functions/client/get-inventory) | Ruft das eigene Inventar des Spielers ab |
| [Get item by name](/de/jaksam-inventory/functions/client/get-item-by-name) | Ruft das erste im eigenen Inventar des Spielers gefundene Item mit diesem Namen ab |
| [Get items by name](/de/jaksam-inventory/functions/client/get-items-by-name) | Ruft alle Items mit passendem Namen aus dem eigenen Inventar des Spielers ab |
| [Get item from slot](/de/jaksam-inventory/functions/client/get-item-from-slot) | Ruft ein Item aus einem bestimmten Slot im Inventar des Spielers ab |
| [Show hotbar](/de/jaksam-inventory/functions/client/show-hotbar) | Zeigt die Hotbar-UI mit den ersten 5 Slots |
| [Set hotbar disabled](/de/jaksam-inventory/functions/client/set-hotbar-disabled) | Aktiviert oder deaktiviert die Hotbar-Funktion |
| [Set hotkeys enabled](/de/jaksam-inventory/functions/client/set-hotkeys-enabled) | Aktiviert oder deaktiviert die Hotkeys (Slots 1-5) |
| [Are hotkeys enabled](/de/jaksam-inventory/functions/client/are-hotkeys-enabled) | Gibt zurück, ob Hotkeys aktuell aktiviert sind |
| [Dequip weapon](/de/jaksam-inventory/functions/client/dequip-weapon) | Legt die aktuell ausgerüstete Waffe ab |
| [Set weapon wheel](/de/jaksam-inventory/functions/client/set-weapon-wheel) | Aktiviert oder deaktiviert das Standard-GTA5-Waffenrad |
| [Set jaksam weapon wheel](/de/jaksam-inventory/functions/client/set-jaksam-weapon-wheel) | Aktiviert oder deaktiviert das radiale jaksam-Waffenrad |
| [Register action button](/de/jaksam-inventory/functions/client/register-action-button) | Registriert einen eigenen Action Button in der Inventar-Toolbar |
| [Unregister action button](/de/jaksam-inventory/functions/client/unregister-action-button) | Entfernt einen zuvor registrierten Action Button |
| [Show action button](/de/jaksam-inventory/functions/client/show-action-button) | Macht einen versteckten Action Button sichtbar |
| [Hide action button](/de/jaksam-inventory/functions/client/hide-action-button) | Versteckt einen Action Button, ohne ihn zu entfernen |
| [Get vehicle inventory limits](/de/jaksam-inventory/functions/client/get-vehicle-inventory-limits) | Gibt Kofferraum-/Handschuhfach-Limits für ein Fahrzeug zurück |
| [Is inventory open](/de/jaksam-inventory/functions/client/is-inventory-open) | Prüft, ob aktuell ein Inventar geöffnet ist |
| [Set inventory disabled](/de/jaksam-inventory/functions/client/set-inventory-disabled) | Deaktiviert oder aktiviert das Öffnen des Inventars vollständig |
| [Is inventory disabled](/de/jaksam-inventory/functions/client/is-inventory-disabled) | Gibt zurück, ob das Öffnen des Inventars aktuell deaktiviert ist |
