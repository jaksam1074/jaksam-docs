---
title: "Türsymbol ändern"
description: "Farbe, Bild und Größe des Tür-Interaktionssymbols anpassen."
icon: "icons"
---

## Wie man die Farbe ändert

Um die Symbolfarben zu ändern, bearbeite die Datei `doors_creator/integrations/cl_integrations.lua` und bearbeite die Zeilen zur Farbe:

```lua
-- r = rot, g = grün, b = blau, a = deckkraft
-- Alle Werte gehen von 0 bis 255
-- Sind alle Farben auf 255 gesetzt, hat das Bild die Standardfarbe
color = {
    r = 50,
    g = 255,
    b = 50,
    a = 255,
}
```

## Wie man das Symbol/Bild ändert

Um das Symbol/Bild zu ändern, ersetze einfach die Bilder im Ordner `doors_creator/icons/`, achte darauf, exakt die gleichen Namen zu verwenden.

## Wie man die Größe ändert

Die Skalierung kann direkt im Ingame-Menü bearbeitet werden, du kannst aber bei Bedarf auch die Werte `x` und `y` in der Datei `doors_creator/integrations/cl_integrations.lua` anpassen:

```lua
-- Bildbreite
x = 0.03,

-- Bildhöhe
y = 0.04,
```
