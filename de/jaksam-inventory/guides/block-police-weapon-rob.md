---
title: "Diebstahl von Polizeiwaffen verhindern"
icon: "user-shield"
description: "Bestimmte Waffen so einschränken, dass nur Spieler mit dem Polizei-Job sie in ihr Inventar verschieben können"
---

Soll sichergestellt sein, dass nur Polizisten Polizeiwaffen in ihr Inventar verschieben können? Diese Anleitung zeigt dir wie, Schritt für Schritt.

Diese Funktion verhindert, dass nicht-Polizei-Spieler Polizeiwaffen in ihr persönliches Inventar verschieben. Versucht ein Spieler, eine Polizeiwaffe zu stehlen, erhält er eine Fehlermeldung und der Transfer wird blockiert.

<Note>
  Diese Funktionalität wird automatisch vom `_hooks/sv_policeonly.lua`-Hook bereitgestellt (falls du ihn bearbeiten willst). Du musst nur deine Waffen als "nur Polizei" markieren.
</Note>

## Schritt-für-Schritt-Anleitung

<Steps>
  <Step title="Items-Datei öffnen">
    Öffne deine Serverdateien und navigiere zu: `jaksam_inventory/_data/items.lua`
  </Step>
  <Step title="Die Waffe finden oder erstellen">
    Finde das Waffen-Item, das du schützen willst (oder erstelle es, falls es nicht existiert).
  </Step>
  <Step title="Als nur-Polizei markieren">
    Füge `policeOnly = true` zur Item-Definition hinzu.
  </Step>
  <Step title="Neu starten">
    Speichere die Datei und starte das Script neu bzw. lade den Server neu.
  </Step>
</Steps>

<Tip>
  Das war's! Jetzt können nur Spieler mit dem Job "police" diese Waffe in ihr persönliches Inventar verschieben.
</Tip>

## Beispiele

### Beispiel 1: Combat Pistol

```lua
['WEAPON_COMBATPISTOL'] = {
    label = 'Combat Pistol',
    weight = 1.0,
    stackable = false,
    close = true,
    description = 'A combat pistol',
    type = 'weapon',
    ammo = 'ammo_9mm',
    throwableOptions = {
        model = nil,
        coords = {x = 0.08, y = 0.03, z = -0.06},
        rot = {x = -25.45, y = -3.76, z = 49.99}
    },
    policeOnly = true  -- Nur Polizei kann diese Waffe verschieben
},
```

### Beispiel 2: Elektroschocker

```lua
['WEAPON_STUNGUN'] = {
    label = 'Stun Gun',
    weight = 1.0,
    stackable = false,
    close = true,
    description = 'A police stun gun',
    type = 'weapon',
    policeOnly = true  -- Nur Polizei kann diese Waffe verschieben
},
```

## Wie es funktioniert

Der `sv_policeonly.lua`-Hook prüft automatisch jedes Mal, wenn jemand versucht, eine Waffe mit `policeOnly = true` in ein Spieler-Inventar zu verschieben. Hat der Spieler nicht den Job "police", wird der Transfer blockiert und er sieht eine Fehlermeldung.

<Warning>
  Das blockiert nur Transfers zu **Spieler-Inventaren**. Polizeiwaffen können weiterhin von jedem zwischen anderen Inventartypen (wie Stashes, Fahrzeuge usw.) verschoben werden.
</Warning>
