---
title: "Fahrzeug-Schloss wechseln"
description: "Wechsle das Schloss eines Fahrzeugs und widerrufe zuvor vom Besitzer geteilte Schlüssel."
icon: "key"
---

Das Auslösen dieses Events (client-seitig) wechselt das Schloss des Fahrzeugs mit diesem Kennzeichen und entfernt alle Schlüssel, die der Besitzer zuvor mit anderen Spielern geteilt hat.

```lua Event
TriggerServerEvent("vehicles_keys:switchLock", plate)
```

### Parameter

| Name    | Datentyp | Beschreibung                |
| ------- | --------- | ------------------------------ |
| `plate` | string    | Das Kennzeichen des Fahrzeugs          |
