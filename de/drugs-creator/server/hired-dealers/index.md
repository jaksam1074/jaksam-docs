---
title: "Angeheuerte Dealer"
description: "NPC-Dealer, die Spieler anheuern, um passiv Drogen in ihren Territorien zu verkaufen."
icon: "user-tie"
---

Angeheuerte Dealer sind NPC-Dealer, die Spieler über das **Trap Phone** anheuern können, um passiv Drogen in Territorien zu verkaufen, die sie besitzen.

Spieler müssen ein [Territorium](/de/drugs-creator/server/territories) besitzen, um darin einen Dealer anzuheuern. Jeder Dealer kann mit Drogen bestückt werden und verkauft diese autonom über die Zeit, wobei sich Einnahmen ansammeln, die der Spieler abholen kann.

Das System umfasst eine **Heat**-Mechanik: Jeder Verkauf erhöht die Heat des Dealers, was die Wahrscheinlichkeit erhöht, dass der Dealer verhaftet oder ausgeraubt wird. Heat baut sich mit der Zeit ab.

## Trap Phone

Das Trap Phone ist ein nutzbares Inventar-Item (`trap_phone`), das das Verwaltungs-UI öffnet. Darüber können Spieler:

- Dealer in eigenen Territorien anheuern und entlassen
- Dealer mit Drogen bestücken
- Einnahmen abholen
- Dealer-Benachrichtigungen einsehen (Verkäufe, Verhaftungen, Raubüberfälle, Territoriumsverlust, ausverkauft)
- Treffen anfragen, um ingame mit einem Dealer zu interagieren
- Territoriums-Informationen einsehen
- Straßenverkauf umschalten (falls aktiviert)

Das Item muss in der Item-Liste deines Frameworks registriert werden — siehe die [Installations](/de/drugs-creator/installation)-Seite für die Item-Definition.

## Konfiguration

Alle Einstellungen für angeheuerte Dealer (Preise, Verkaufsintervalle, maximale Dealer, Heat-System, akzeptierte Drogen) werden über das Ingame-Menü `/drugscreator` verwaltet.
