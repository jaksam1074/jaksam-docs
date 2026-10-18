---
title: "Einstellungen im Spiel"
description: "Gebühren, Ämter, Werkstätten, Preise, Löhne und Razzia-Regeln im Spiel mit /documents config ändern, ohne Neustart."
icon: "sliders"
---

Admins ändern die meisten Einstellungen im Spiel mit `/documents config`: keine Datei zu bearbeiten, kein Neustart.

## Was drin ist

| Bereich | Einstellungen |
| --- | --- |
| **Allgemein** | Dokumente benutzen und zeigen, Dokumentnummern, Sprache |
| **Ämter** | Starter-Dokumente, Gebühren, die Ämter selbst |
| **Werkstätten** | Die Werkstätten mit Preis und Besitzer, Regeln für Kauf und Verkauf, Upgrade-Preise, Materialbestellungen, Lager, Regeln für Fälschen und Aufträge |
| **Arbeiter** | Einstellgebühren, Löhne, Arbeitszeiten, Demo-Modus |
| **Razzien** | Regeln, Einheiten mit ihren Asservatenschränken, die Tür, Beschlagnahme |

## So funktioniert es

- **Änderungen werden gesammelt und zusammen angewendet.** Was du änderst, wird markiert, und eine Leiste unten speichert alles (**Apply**) oder verwirft es (**Discard**). Vorher erreicht nichts die Spieler.
- **Orte werden mit der Kamera gesetzt.** **Place** lässt dich herumgehen und zielen: Ein Geist des NPCs steht, wo du hinsiehst, das Mausrad dreht ihn, ein Klick übernimmt den Ort. **Here** nimmt die Stelle, an der du stehst, und du kannst dich zu einem gespeicherten Ort teleportieren.
- **Jobs werden aus der Liste des Frameworks gewählt.** Zeiten werden in Sekunden, Minuten, Stunden oder Tagen angezeigt, Chancen in Prozent.
- **Sofort wirksam** für alle auf dem Server nach **Apply**. Eine markierte Ausnahme wartet auf den nächsten Start des Scripts: die Lagergrößen.
- **Die Sprache** wechselt sofort für alle: Menüs, Targets, Blips und die Labels in der Config.

## Dateien und Datenbank

Die Config-Dateien bleiben die Standardwerte. Ein geänderter Wert wird in der Datenbank gespeichert (Tabelle `jksm_identity_settings`) und hat Vorrang vor der Datei. Jeder Wert kann mit einem Klick auf seinen Standard zurück, und jede Änderung wird mit dem Admin, der sie gemacht hat, ins Log geschrieben.

<Note>
  Diese bleiben in `config/main.lua`, weil sie beim Laden des Scripts gebraucht werden: Framework, Inventar und Target, die Admin-Rechte, `Config.Debug` und die Item-Namen.
</Note>
