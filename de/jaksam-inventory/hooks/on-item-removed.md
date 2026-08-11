---
title: "Item removed"
description: "Hook, der ausgelöst wird, wenn ein Item aus einem Inventar entfernt wird."
icon: "circle-minus"
---

Wird ausgelöst, wenn ein Item aus einem Inventar entfernt wird. Registriere mit [`registerHook`](/de/jaksam-inventory/hooks#register-a-hook) unter dem Event-Namen `onItemRemoved`.

### Payload

| Feld | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string | z.B. `"player:1"` |
| `itemName` | string | z.B. `"bread"` |
| `amount` | number | Entfernte Menge |
| `metadata` | table \| nil | Item-Metadaten |
| `slotId` | number | Slot, aus dem das Item entfernt wurde |

<Info>
  [TODO: INFORMATION NEEDED] Das Quellmaterial enthielt kein eigenes Beispiel für diesen speziellen Hook. Siehe [Hooks-Übersicht](/de/jaksam-inventory/hooks) für das allgemeine `registerHook`-Muster und die Filter, die hier genauso gelten.
</Info>
