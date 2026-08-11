---
title: "Standard-Search-Action ersetzen"
description: "Verwende eine eigene Search-Action anstelle der Standardaktion, indem du ein Search-Modul erstellst."
icon: "magnifying-glass"
---

Standardmäßig verwendet die Search-Action das eingebaute Suchverhalten von Jobs Creator. Wenn du stattdessen dein eigenes Stash-, Safe- oder Armory-System verwenden möchtest, kannst du sie durch ein eigenes **Modul** ersetzen.

## So ersetzt du es

<Steps>
  <Step title="Zum Modules-Ordner navigieren">
    Gehe zum Ordner `jobs_creator/_modules`.
  </Step>
  <Step title="Den Search-Modultyp finden">
    Suche das vorhandene Modul vom Typ **search** als Vorlage.
  </Step>
  <Step title="Das Modul duplizieren">
    Kopiere das vorhandene Search-Modul und füge es im gleichen Ordner ein.
  </Step>
  <Step title="Die Kopie umbenennen">
    Benenne die eingefügte Kopie passend zu deiner Integration um (z.B. `my_stash_search.lua`).
  </Step>
  <Step title="Die Datei öffnen">
    Öffne die neu umbenannte Datei.
  </Step>
  <Step title="Die Events anpassen">
    Bearbeite den Inhalt der Datei, sodass sie die Events/Exports deines eigenen Stash-, Safe- oder Armory-Scripts anstelle der Standardwerte aufruft.
  </Step>
  <Step title="Das Modul ingame auswählen">
    Öffne das `/jobscreator`-Menü, gehe zu den Einstellungen und wähle dein neues Modul für den Job aus.
  </Step>
</Steps>

<Note>
  Für mehr Details darüber, wie Module allgemein funktionieren, siehe die [Module](/de/jobs-creator/modules)-Seite.
</Note>
