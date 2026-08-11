---
title: "QBCore Jobs Injection"
description: "Behebe, dass andere Scripts Jobs-Creator-Jobs auf QBCore aufgrund der Script-Startreihenfolge nicht erkennen."
icon: "plug"
---

Normalerweise musst du keinen Code hinzufügen. Trotzdem können unterschiedliche Script-Startreihenfolgen dazu führen, dass andere Scripts die Jobs-Creator-Jobs auf QBCore nicht erkennen.

## Wie kann ich das beheben?

Die Lösung ist ganz einfach — füge das folgende Event client- und serverseitig in dem Script hinzu, das die Jobs-Creator-Jobs nicht erkennt:

```lua
-- jaksam's Jobs Creator Integration
AddEventHandler('jobs_creator:injectJobs', function(jobs)
    -- Weise die neuen Jobs dem QBCore-Objekt zu, die folgende Zeile hängt davon ab, wie dein Script aufgebaut ist
    QBCore.Shared.Jobs = jobs
end)
```
