---
title: "Benachrichtigungen ersetzen"
description: "Verwende ein eigenes Benachrichtigungssystem anstelle des Standardsystems, indem du ein Notify-Modul erstellst."
icon: "bell"
---

Wird verwendet, um die normalen Benachrichtigungen anzuzeigen, zum Beispiel `"You are not on duty"`. Das sind die normalen Benachrichtigungen, kein TextUI, aber der Ablauf ist für beide gleich.

## So ersetzt du es

<Steps>
  <Step title="Zum Modules-Ordner navigieren">
    Gehe zum Ordner `jobs_creator/_modules`.
  </Step>
  <Step title="Den Notify-Modultyp finden">
    Suche das vorhandene Modul vom Typ **notify** als Vorlage.
  </Step>
  <Step title="Das Modul duplizieren">
    Kopiere das vorhandene Notify-Modul und füge es im gleichen Ordner ein.
  </Step>
  <Step title="Die Kopie umbenennen">
    Benenne die eingefügte Kopie passend zu deiner Integration um (z.B. `my_notify.lua`).
  </Step>
  <Step title="Die Datei öffnen">
    Öffne die neu umbenannte Datei.
  </Step>
  <Step title="Die Events anpassen">
    Bearbeite den Inhalt der Datei, sodass sie die Events/Exports deines eigenen Benachrichtigungs-Scripts anstelle der Standardwerte aufruft.
  </Step>
  <Step title="Das Modul ingame auswählen">
    Öffne das `/jobscreator`-Menü, gehe zu den Einstellungen und wähle dein neues Modul für den Job aus.
  </Step>
</Steps>

<Note>
  Für mehr Details darüber, wie Module allgemein funktionieren, siehe die [Module](/de/jobs-creator/modules)-Seite.
</Note>
