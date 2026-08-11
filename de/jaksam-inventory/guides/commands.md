---
title: "Commands"
icon: "slash-forward"
description: "Vollständige Liste der Admin-Befehle zur Verwaltung von Items, Inventaren und Stashes"
---

# Admin-Befehle

<Note>
  Alle Admin-Befehle benötigen die **ACE-Berechtigung**. Nutze `/inventory`, um zu prüfen, ob du sie hast.
</Note>

## `/inventory`

Öffnet das Admin-Menü zur Verwaltung von Items, Shops, Stashes, zum Einsehen von Statistiken usw.

## `/giveitem`

Gibt Items an einen Spieler oder ein Inventar.

<ParamField path="inventoryId|playerId|'me'" type="string" required>
  Ziel-Inventar, Spieler-ID oder `me` für dich selbst
</ParamField>

<ParamField path="itemName" type="string" required>
  Name des zu gebenden Items
</ParamField>

<ParamField path="amount" type="number" required>
  Zu gebende Menge
</ParamField>

<ParamField path="slotId" type="number">
  Optionaler bestimmter Slot, in den das Item platziert werden soll
</ParamField>

```bash
/giveitem me bread 10                     # Gibt dir selbst 10 Brot
/giveitem 1 water 5                       # Gibt Spieler 1 5 Wasser
/giveitem stash_police weapon_pistol 1 3  # Gibt stash_police 1 weapon_pistol in Slot 3
```

## `/removeitem`

Entfernt Items von einem Spieler oder Inventar.

<ParamField path="inventoryId" type="string" required>
  Ziel-Inventar oder Spieler-ID
</ParamField>

<ParamField path="itemName" type="string" required>
  Name des zu entfernenden Items
</ParamField>

<ParamField path="amount" type="number" required>
  Zu entfernende Menge
</ParamField>

<ParamField path="slotId" type="number">
  Optionaler bestimmter Slot, aus dem entfernt werden soll
</ParamField>

```bash
/removeitem 1 bread 10                    # Entfernt 10 Brot aus dem Inventar von Spieler 1
/removeitem stash_police weapon_pistol 1  # Entfernt 1 weapon_pistol aus stash_police
```

## `/clearinventory`

Entfernt alle Items aus einem Inventar. Ist `inventoryId` leer, wird dein eigenes Inventar geleert. Du kannst auch ein Item vom Leeren ausschließen.

<ParamField path="inventoryId" type="string">
  Ziel-Inventar. Standardmäßig dein eigenes Inventar, wenn nicht angegeben
</ParamField>

<ParamField path="excludedItemName" type="string">
  Item, das behalten werden soll, wird vom Leeren ausgeschlossen
</ParamField>

```bash
/clearinventory          # Leert dein Inventar
/clearinventory 1        # Leert das Inventar von Spieler 1
/clearinventory 2 phone  # Leert das Inventar von Spieler 2, behält aber das Telefon
```

## `/openinventory`

Öffnet das Inventar eines anderen Spielers.

<ParamField path="targetPlayerId" type="number" required>
  ID des Spielers, dessen Inventar geöffnet werden soll
</ParamField>

```bash
/openinventory 1  # Öffnet das Inventar von Spieler 1
```

## `/saveinventories`

Erzwingt das Speichern aller geänderten Inventare in der Datenbank.

<CardGroup cols={2}>
  <Card title="Inventarverwaltung" icon="box-open">
    `/inventory`, `/giveitem`, `/removeitem`, `/clearinventory`
  </Card>

  <Card title="Spieleraktionen" icon="user">
    `/openinventory`, `/saveinventories`
  </Card>
</CardGroup>
