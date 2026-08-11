---
title: "Admin-Inventar (Omnipack)"
description: "Auf das Admin-Omnipack zugreifen und es verwalten, sowie reine Omnipack-Berechtigungen einrichten"
icon: "warehouse"
---

Falls du bereits Admin-Berechtigungen hast (erkennbar daran, dass `/inventory` im Spiel funktioniert), kannst du das Omnipack einfach öffnen, indem du dein Inventar öffnest (F2) und dann F1 drückst.

<Warning>
  Einen Gegenstand **IN** das Omnipack zu verschieben, **löscht** ihn.
</Warning>

<Frame>
  ![Omnipack screenshot](/images/omnipack-screenshot.png)
</Frame>

## Nur-Omnipack-Zugriff

Falls du **nur** Zugriff aufs Omnipack geben willst, ohne Zugriff auf das Adminmenü und die Befehle zu gewähren, nutze diese spezifische Berechtigung:

```bash
add_ace identifier.license:26240584e4v4ca31b22d247b8be6921a8d22j6m1 jaksam_inventory.omnipack allow # Erlaubt nur die Omnipack-Berechtigung
```

Mit dieser Berechtigung kann der Spieler:

<CardGroup cols={2}>
  <Card title="Kann" icon="check">
    Das Omnipack nutzen (F1 im Inventar)
  </Card>

  <Card title="Kann nicht" icon="xmark">
    Das Adminmenü öffnen (`/inventory`)

    Admin-Befehle nutzen (`/giveitem`, `/removeitem`, usw.)
  </Card>
</CardGroup>
