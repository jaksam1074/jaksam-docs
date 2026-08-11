---
title: "Server"
icon: "server"
description: "Vollständige Referenz der server-seitigen Exports zur Verwaltung von Inventaren, Items, Stashes und Fahrzeugen"
---

## Kompatibilität

Dieses Script funktioniert mit anderen beliebten Inventarsystemen wie es_extended, qb-inventory und ox_inventory.

<Info>
  Für ESX- und QBCore-Funktionen erfolgt die Einrichtung automatisch. Willst du aber weiterhin Exports von ox_inventory oder qb-inventory für Kompatibilität nutzen, musst du diese Option in der Datei `jaksam_inventory/integrations/sv_integrations.lua` aktivieren.
</Info>

## Server-Funktionen

| Funktion | Beschreibung |
| --- | --- |
| [Add item](/de/jaksam-inventory/functions/server/add-item) | Fügt Items zu einem Inventar hinzu |
| [Add item to trunk](/de/jaksam-inventory/functions/server/add-item-to-trunk) | Fügt Items zu einem Fahrzeugkofferraum anhand des Kennzeichens hinzu |
| [Add item to glovebox](/de/jaksam-inventory/functions/server/add-item-to-glovebox) | Fügt Items zu einem Fahrzeug-Handschuhfach anhand des Kennzeichens hinzu |
| [Remove item from trunk](/de/jaksam-inventory/functions/server/remove-item-from-trunk) | Entfernt Items aus einem Fahrzeugkofferraum anhand des Kennzeichens |
| [Remove item from glovebox](/de/jaksam-inventory/functions/server/remove-item-from-glovebox) | Entfernt Items aus einem Fahrzeug-Handschuhfach anhand des Kennzeichens |
| [Get inventory ID from plate](/de/jaksam-inventory/functions/server/get-inventory-id-from-plate) | Löst die vollständige Inventar-ID für eine Fahrzeugabteilung auf |
| [Can carry item](/de/jaksam-inventory/functions/server/can-carry-item) | Prüft, ob ein Inventar Platz für zusätzliche Items hat |
| [Can swap item](/de/jaksam-inventory/functions/server/can-swap-item) | Prüft, ob der Tausch zweier Items möglich ist |
| [Clear inventory](/de/jaksam-inventory/functions/server/clear-inventory) | Entfernt alle Items aus einem Inventar |
| [Create inventory](/de/jaksam-inventory/functions/server/create-inventory) | Erstellt ein neues Inventar in Datenbank und/oder Speicher |
| [Force open inventory](/de/jaksam-inventory/functions/server/force-open-inventory) | Erzwingt das Öffnen eines Inventars für einen bestimmten Spieler |
| [Get inventory](/de/jaksam-inventory/functions/server/get-inventory) | Ruft vollständige Daten über ein Inventar ab |
| [Get item from slot](/de/jaksam-inventory/functions/server/get-item-from-slot) | Ruft ein Item aus einem bestimmten Slot ab |
| [Get item by name](/de/jaksam-inventory/functions/server/get-item-by-name) | Ruft das erste Item mit passendem Namen ab |
| [Get items by name](/de/jaksam-inventory/functions/server/get-items-by-name) | Ruft alle Items mit passendem Namen ab |
| [Get item label](/de/jaksam-inventory/functions/server/get-item-label) | Ruft das Anzeige-Label eines Items ab |
| [Get total item amount](/de/jaksam-inventory/functions/server/get-total-item-amount) | Gibt die Gesamtmenge eines Items zurück, inklusive Behälter |
| [Has item](/de/jaksam-inventory/functions/server/has-item) | Prüft, ob ein Inventar ein bestimmtes Item hat |
| [Register usable item](/de/jaksam-inventory/functions/server/register-usable-item) | Registriert einen Callback für die Nutzung eines Items |
| [Register stash](/de/jaksam-inventory/functions/server/register-stash) | Registriert dynamisch einen neuen Stash |
| [Register item](/de/jaksam-inventory/functions/server/register-item) | Registriert zur Laufzeit eine neue Item-Definition |
| [Remove item](/de/jaksam-inventory/functions/server/remove-item) | Entfernt Items aus einem Inventar |
| [Save dirty inventories](/de/jaksam-inventory/functions/server/save-dirty-inventories) | Speichert alle geänderten Inventare in der Datenbank |
| [Save dirty inventory](/de/jaksam-inventory/functions/server/save-dirty-inventory) | Speichert ein bestimmtes Inventar in der Datenbank |
| [Set inventory max weight](/de/jaksam-inventory/functions/server/set-inventory-max-weight) | Setzt die maximale Gewichtskapazität für ein Inventar |
| [Set item metadata in slot](/de/jaksam-inventory/functions/server/set-item-metadata-in-slot) | Aktualisiert die Metadaten eines Items in einem Slot |
| [Set durability](/de/jaksam-inventory/functions/server/set-durability) | Setzt den Haltbarkeitswert eines Items in einem Slot |
