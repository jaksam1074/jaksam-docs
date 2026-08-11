---
title: "Crafting-Rezepte (Drag & Drop)"
icon: "flask-gear"
description: "Spieler Items craften lassen, indem sie ein Item über ein anderes ziehen, mit dem eingebauten Crafting-Hook"
---

Sollen Spieler Items craften können, indem sie ein Item über ein anderes ziehen? Diese Anleitung zeigt dir wie, Schritt für Schritt.

Diese Funktion erlaubt Spielern, Items zu craften, indem sie ein Quell-Item über ein Ziel-Item im selben Inventar ziehen. Passt das Rezept, werden die Items kombiniert und das Ergebnis erstellt.

<Note>
  Diese Funktionalität wird vom `_hooks/sv_craftings.lua`-Hook bereitgestellt. Du musst nur deine Rezepte zur `CRAFTING_RECIPES`-Tabelle hinzufügen.
</Note>

## Wie es funktioniert

<Steps>
  <Step title="Quelle auf Ziel ziehen">
    Der Spieler zieht ein **Quell-Item** über ein **Ziel-Item** im selben Inventar.
  </Step>
  <Step title="Rezept-Prüfung">
    Das System prüft, ob es ein passendes Rezept gibt.
  </Step>
  <Step title="Crafting passiert">
    Passt das Rezept und sind die Mengen ausreichend, wird gecraftet.
  </Step>
  <Step title="Items werden verbraucht">
    Quell- und/oder Ziel-Items werden entfernt (je nach Rezept-Einstellungen).
  </Step>
  <Step title="Ergebnis wird hinzugefügt">
    Das Ergebnis-Item wird dem Inventar hinzugefügt.
  </Step>
</Steps>

## Schritt-für-Schritt-Anleitung

<Steps>
  <Step title="Crafting-Hook öffnen">
    Navigiere zu: `jaksam_inventory/_hooks/sv_craftings.lua`
  </Step>
  <Step title="Die Rezepte-Tabelle finden">
    Finde die `CRAFTING_RECIPES`-Tabelle (sie ist nahe dem Anfang der Datei).
  </Step>
  <Step title="Dein Rezept hinzufügen">
    Füge dein Rezept nach diesem Format hinzu:

    ```lua
        local CRAFTING_RECIPES = {
            ["source_item_name"] = {
                sourceQuantityRequired = 1,        -- Wie viele Quell-Items benötigt werden
                sourceIsToRemove = true,           -- Quell-Item nach dem Craften entfernen?
                targetItem = "target_item_name",  -- Name des Ziel-Items
                targetQuantity = 1,                -- Wie viele Ziel-Items benötigt werden
                targetIsToRemove = true,           -- Ziel-Item nach dem Craften entfernen?
                resultItem = "result_item_name",  -- Name des erstellten Items
                resultQuantity = 1,                -- Wie viele Ergebnis-Items erstellt werden
            },
        }
    ```
  </Step>
  <Step title="Neu starten">
    Speichere die Datei und starte das Script neu bzw. lade den Server neu.
  </Step>
</Steps>

<Tip>
  Das war's! Jetzt können Spieler das Quell-Item über das Ziel-Item ziehen, um zu craften.
</Tip>

## Rezept-Eigenschaften erklärt

<ParamField path="sourceQuantityRequired" type="number">
  Wie viele des Quell-Items für das Rezept benötigt werden
</ParamField>

<ParamField path="sourceIsToRemove" type="boolean">
  Auf `true` setzen, falls das Quell-Item nach dem Craften entfernt werden soll, `false` um es zu behalten
</ParamField>

<ParamField path="targetItem" type="string">
  Der exakte Name (wie in `items.lua` definiert) des Items, auf das du das Quell-Item ziehst
</ParamField>

<ParamField path="targetQuantity" type="number">
  Wie viele des Ziel-Items für das Rezept benötigt werden
</ParamField>

<ParamField path="targetIsToRemove" type="boolean">
  Auf `true` setzen, falls das Ziel-Item nach dem Craften entfernt werden soll, `false` um es zu behalten
</ParamField>

<ParamField path="resultItem" type="string">
  Der exakte Name (wie in `items.lua` definiert) des Items, das erstellt wird
</ParamField>

<ParamField path="resultQuantity" type="number">
  Wie viele Ergebnis-Items erstellt werden
</ParamField>

## Beispiele

<Tabs>
  <Tab title="Zielfernrohr zu Thermal upgraden">
    Kombiniere einen Schraubenschlüssel mit einem erweiterten Zielfernrohr zu einem Thermal-Zielfernrohr:

    ```lua
        ["weapon_wrench"] = {
            sourceQuantityRequired = 1,
            sourceIsToRemove = false,              -- Schraubenschlüssel behalten (wiederverwendbares Werkzeug)
            targetItem = "advanced_scope",
            targetQuantity = 1,
            targetIsToRemove = true,               -- Erweitertes Zielfernrohr entfernen
            resultItem = "thermal_scope",
            resultQuantity = 1,
        },
    ```

    **So wird's genutzt:** Schraubenschlüssel auf das erweiterte Zielfernrohr ziehen → Thermal-Zielfernrohr wird erstellt, Schraubenschlüssel bleibt, erweitertes Zielfernrohr wird entfernt.
  </Tab>
  <Tab title="Materialien kombinieren">
    Kombiniere 2 Holzstücke mit 1 Nagel zu einem Holzbrett:

    ```lua
        ["wood"] = {
            sourceQuantityRequired = 2,
            sourceIsToRemove = true,               -- Die 2 Holzstücke entfernen
            targetItem = "nail",
            targetQuantity = 1,
            targetIsToRemove = true,               -- Den Nagel entfernen
            resultItem = "wooden_plank",
            resultQuantity = 1,
        },
    ```

    **So wird's genutzt:** 2 Holz-Items über 1 Nagel ziehen → Holzbrett wird erstellt, beide Materialien werden verbraucht.
  </Tab>
</Tabs>

## Wichtige Hinweise

<CardGroup cols={2}>
  <Card title="Nur im gleichen Inventar" icon="box">
    Crafting funktioniert nur, wenn sich beide Items im **gleichen Inventar** befinden (nicht vom Spieler-Inventar ins Fahrzeug-Inventar ziehen)
  </Card>

  <Card title="Item-Namen müssen übereinstimmen" icon="fingerprint">
    Die Namen `targetItem` und `resultItem` müssen exakt mit den Item-Namen in `_data/items.lua` übereinstimmen
  </Card>

  <Card title="Mengenprüfung" icon="calculator">
    Das System prüft automatisch, ob du genug Items hast, bevor gecraftet wird
  </Card>

  <Card title="Mehrere Rezepte" icon="layer-group">
    Du kannst so viele Rezepte hinzufügen, wie du willst, zur `CRAFTING_RECIPES`-Tabelle
  </Card>
</CardGroup>

<Warning>
  **Eine Quelle, mehrere Ziele:** Jedes Quell-Item kann nur ein Rezept haben. Brauchst du mehrere Rezepte für das gleiche Quell-Item, musst du unterschiedliche Quell-Items nutzen oder separate Crafting-Systeme erstellen.
</Warning>
