---
title: "Module"
description: "Ersetze Standard-Funktionen wie Notify, Fortschrittsbalken, Stash und Logs durch deine eigenen Module."
icon: "puzzle-piece"
---

Module sind ein einfacher Weg für Drugs Creator, bestimmte Standard-Funktionen (Notify, Fortschrittsbalken, Stash, Logs) zu ersetzen.

Um ein bereits vorhandenes Modul auszuwählen, öffne das `/drugscreator`-Menü, gehe zu den Einstellungen und wähle es aus. So einfach ist das.

### Wie erstelle ich ein eigenes Modul?

Ein Modul zu erstellen ist extrem einfach:

<Steps>
  <Step title="Zum Modules-Ordner navigieren">
    Gehe zum Ordner `drugs_creator/_modules`.
  </Step>
  <Step title="Modultyp auswählen">
    Wähle den Modultyp, den du erstellen möchtest (Logs, Fortschrittsbalken, Stash, usw.).
  </Step>
  <Step title="Vorhandenes Modul duplizieren">
    Kopiere ein vorhandenes Modul und füge es im gleichen Ordner als Vorlage ein.
  </Step>
  <Step title="Die Kopie umbenennen">
    Benenne die eingefügte Kopie passend zur Integration um, die du erstellen möchtest.
  </Step>
  <Step title="Die Datei öffnen">
    Öffne die neu umbenannte Datei.
  </Step>
  <Step title="Die Events anpassen">
    Bearbeite den Inhalt der Datei passend zu den Events des Drittanbieter-Scripts, das du integrierst.
  </Step>
</Steps>

### Verfügbare Module

| Kategorie | Verfügbare Optionen |
| --- | --- |
| Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Gangs | `default` |
| Inventory | `jaksam_inventory`, `ox_inventory`, `qb-inventory` |
| Logs | `custom`, `jaksam` |
| Menü | `menu_default`, `ox_context`, `ox_lib` |
| Fortschrittsbalken | `jaksam`, `ox_lib`, `qb-core` |
| Stash | `jaksam_inventory`, `ox-inventory`, `qb-inventory` |
| Text UI | `esx`, `none`, `ox_lib` |
