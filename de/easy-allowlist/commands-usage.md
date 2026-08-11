---
title: "Befehlsnutzung"
description: "Konsolen- und Ingame-Befehle zur Verwaltung von Allowlist und Warteschlangen-Priorität."
icon: "terminal"
---

Alle Befehle können entweder im Spiel von Server-Admins oder direkt über die Serverkonsole genutzt werden.

### Allowlist hinzufügen

```
/add_allowlist identifier/requestId
```

Der Parameter kann entweder eine Identifier **oder** eine Request-ID sein.

| Parameter    | Typ     | Beschreibung                                                                                                                        |
| ------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `identifier` | string  | Die **Haupt**-Identifier des Spielers (kann Steam-Hex, Rockstar-Lizenz oder Discord-ID sein). Nutze die in den Script-Einstellungen konfigurierte Identifier. |
| `requestId`  | integer | Die ID der Anfrage. Das ist die ID, die Spielern nach dem Senden der Allowlist-Anfrage angezeigt wird.                                       |

#### Beispiel

```
/add_allowlist 7b1261c1ae07dr156af762fcb1bec11a403b9413
```

### Allowlist entfernen

```
/remove_allowlist identifier
```

Der Parameter **muss** die Haupt-Identifier des Spielers sein.

| Parameter    | Typ    | Beschreibung                                                                                                                        |
| ------------ | ------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `identifier` | string | Die **Haupt**-Identifier des Spielers (kann Steam-Hex, Rockstar-Lizenz oder Discord-ID sein). Nutze die in den Script-Einstellungen konfigurierte Identifier. |

#### Beispiel

```
/remove_allowlist 7b1261c1ae07dr156af762fcb1bec11a403b9413
```

### Warteschlangen-Priorität setzen

```
/set_queue_priority identifier/playerId priority
```

Der **erste** Parameter kann eine Haupt-Identifier **oder** eine Spieler-ID sein (falls der Spieler online ist).

| Parameter    | Typ     | Beschreibung                                                                                                                        |
| ------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `identifier` | string  | Die **Haupt**-Identifier des Spielers (kann Steam-Hex, Rockstar-Lizenz oder Discord-ID sein). Nutze die in den Script-Einstellungen konfigurierte Identifier. |
| `playerId`   | integer | Die Server-ID des Spielers.                                                                                                          |
| `priority`   | integer | Die Priorität des Spielers. Höhere Zahl = mehr Priorität.                                                                            |

#### Beispiel

```
/set_queue_priority 7b1261c1ae07dr156af762fcb1bec11a403b9413 15
```
