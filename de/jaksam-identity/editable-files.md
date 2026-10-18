---
title: "Editierbare Dateien"
description: "Die Dateien von Jaksam Identity, die im verschlüsselten Release offen bleiben: config, locales, bridge und editierbare Hooks."
icon: "file-pen"
---

Jaksam Identity hat keinen `integrations`-Ordner. Alles, was du ändern kannst, bleibt im verschlüsselten Release offen, in diesen Ordnern:

| Ordner | Was |
| --- | --- |
| `config/` | Alle Einstellungen |
| `locales/` | Texte, `Config.Locale` wählt die Sprache |
| `bridge/` | Inventar, Target, Benachrichtigungen, Handy (die Framework-Bridge in `bridge/framework/` ist verschlüsselt) |
| `editable/` | Hooks: `CanIssue`, `OnIssued`, `CanEnterWorkshop`, `CanRaid`, `OnRaid`, `OnForged`, `OnLog`, `SkillCheck`, `Progress` |
| `install/` | Inventar-Items, Item-Typen, Bilder, SQL |

## Editierbare Hooks

<CardGroup cols={2}>
  <Card title="editable/server.lua" icon="server" href="/de/jaksam-identity/server/hooks">
    Server-Hooks: wer ausstellen, eine Werkstatt betreten oder stürmen darf, und was nach einer Ausstellung, einer Fälschung, einem Razzia-Schritt oder einer Log-Zeile passiert.
  </Card>

  <Card title="editable/client.lua" icon="laptop" href="/de/jaksam-identity/client">
    Client-Hooks: der Skill-Check an den Fälscherstationen und der Fortschrittsbalken.
  </Card>
</CardGroup>

Ändere den Inhalt nach deinem Server, aber **behalte die Funktionsnamen und Argumente**.

## Bridge

`Config.Bridge` in `config/main.lua` wählt die Dateien in `bridge/`:

```lua
Config.Bridge = {
    framework = 'esx',          -- ESX version: 'esx' | QBCore version: 'auto' | 'qb' | 'qbox'
    inventory = 'jaksam',       -- 'jaksam' | 'ox_inventory' | 'qb-inventory' (QBCore version)
    target = 'ox_target',       -- 'ox_target' | QBCore version also 'qb-target' | 'auto'
    notify = 'esx',             -- 'esx' | 'qb' | 'qbox' | 'ox_lib' | QBCore version also 'auto'
    phone = 'roadphone',        -- 'roadphone' | 'none'
    menu = 'jksm',              -- 'jksm' (interaction card) | 'ox_lib' (context menu)
}
```

Um ein anderes Inventar zu unterstützen: Der Vertrag, den eine Inventar-Bridge erfüllen muss, ist oben in `bridge/inventory/jaksam.lua` dokumentiert.
