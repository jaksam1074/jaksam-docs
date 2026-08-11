---
title: "Get item image path"
description: "Ruft den NUI-Bildpfad für ein Item ab, mit Fallback auf ein Standardbild, falls keines gefunden wird."
icon: "image"
---

Ruft den NUI-Bildpfad für ein Item ab. Die Funktion nutzt ein Fallback-System: prüft zuerst, ob das Item ein eigenes `image`-Feld hat, versucht dann `.png`- oder `.webp`-Dateien zu finden, und greift schließlich auf das Standardbild `box.webp` zurück.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemImagePath(itemName)
```

```lua Example
local imagePath = exports['jaksam_inventory']:getItemImagePath('bread')
print(imagePath) -- nui://jaksam_inventory/_images/bread.png

-- Item mit eigenem image-Feld
local customImage = exports['jaksam_inventory']:getItemImagePath('custom_item')
print(customImage) -- nui://jaksam_inventory/_images/custom_image.png (falls item.image gesetzt ist)

-- Nicht gefundenes Item gibt das Standard-Box-Bild zurück
local notFound = exports['jaksam_inventory']:getItemImagePath('invalid_item')
print(notFound) -- nui://jaksam_inventory/_images/box.webp
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `itemName` | string | Der Name des Items, dessen Bildpfad abgerufen werden soll |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `imagePath` | string | Der NUI-Bildpfad (z.B. "nui://jaksam_inventory/_images/bread.png"). Gibt immer einen gültigen Pfad zurück, mit Fallback auf `box.webp`, falls das Item nicht existiert oder kein Bild gefunden wird |
