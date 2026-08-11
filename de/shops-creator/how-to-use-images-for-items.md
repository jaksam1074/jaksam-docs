---
title: "Wie man Bilder für Items nutzt"
description: "Eigene Item-Bilder konfigurieren, die in der Shop-UI angezeigt werden."
icon: "image"
---

## Allgemeine Methode

Das Script erlaubt dir, beliebige Bilder für die Items zu nutzen, gebunden an deren Namen — heißt ein Item `bread`, muss das Bild `bread.png` heißen.

Du kannst die gewünschten Bilder im Ordner `shops_creator/html/images/` ablegen.

## Ich will die Bilddateien aus einem Inventar beziehen

Um den Standardpfad anzupassen, in dem das Script nach Bildern sucht, öffne die Datei `shops_creator/integrations/cl_integrations.lua` und bearbeite die Variable `IMAGES_PATH` nach Belieben.
