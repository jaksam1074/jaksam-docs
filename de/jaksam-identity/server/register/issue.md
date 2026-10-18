---
title: "Ausstellen"
description: "Einem Spieler ein echtes Dokument ausstellen und in sein Inventar legen."
icon: "id-card"
---

Stellt ein echtes Dokument aus: schreibt es ins Register, nimmt das Foto auf, legt das Item ins Inventar des Spielers und markiert das ältere gültige Dokument desselben Typs als `replaced`.

<CodeGroup>

```lua Export
exports["jksm_identity"]:Issue(playerId, typeId, options)
```

```lua Example
-- A DMV script issuing the driver licence after a passed test
local serial, reason = exports["jksm_identity"]:Issue(playerId, "drive", {
    issuerSrc = instructorId,
    grant = { "drive" },
})

if serial then
    print("Issued driver licence " .. serial)
else
    print("Not issued: " .. reason)
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers, der das Dokument bekommt |
| `typeId` | string | Der Dokumenttyp, ein Schlüssel von `Config.Documents` (zum Beispiel `id_card`, `drive`, `weapon`, `badge_pd`) |
| `options` | table (optional) | Siehe unten |

### Optionen

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `issuerSrc` | integer | Server-ID des Spielers, der es ausstellt. Zuerst wird `Editable.CanIssue` gefragt, und der Aussteller wird ins Register geschrieben. `0` steht für die Konsole |
| `grant` | table | Lizenztypen, die der Charakter vor der Ausstellung bekommt, zum Beispiel `{ "drive", "drive_truck" }`. Müssen Lizenzen dieses Dokuments sein |
| `force` | boolean | Auch ausstellen, wenn die Lizenz (`license`-Dokumente) oder der Job (`badge`-Dokumente) fehlt |
| `photo` | boolean | `false`, um ohne Foto auszustellen |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `serial` | string \| nil | Die neue Dokumentnummer, oder **nil**, wenn es nicht ausgestellt wurde |
| `reason` | string \| nil | Warum es nicht ausgestellt wurde: `unknown_type`, `no_player`, `not_allowed`, `license_missing`, `wrong_job`, `busy` (ein Foto dieses Spielers wird gerade aufgenommen), `additem_<code>` (das Inventar hat das Item abgelehnt) |

<Note>
  Das Foto wird vom Charakter des Spielers aufgenommen, der Aufruf wartet also darauf. Rufe ihn aus einem Thread oder Event-Handler auf, nicht aus Code, der sofort zurückkehren muss.
</Note>
