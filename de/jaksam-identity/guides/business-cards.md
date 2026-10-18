---
title: "Visitenkarten"
description: "Lass jeden Job eigene Visitenkarten mit Name, Titel, Telefonnummer und einer freien Zeile drucken."
icon: "address-card"
---

Jeder Job druckt seine eigenen Visitenkarten, im eigenen Design. Spieler öffnen den Druckdialog mit `/businesscards` und bekommen einen Stapel Karten mit:

- ihrem Namen
- einem frei wählbaren Titel
- ihrer Telefonnummer (von RoadPhone vorausgefüllt, wenn `Config.Bridge.phone = 'roadphone'`)
- einer freien Zeile

Visitenkarten haben kein Register und keine Nummer. Eine Visitenkarte kann angesehen, gezeigt oder dem nächsten Spieler übergeben werden.

## Konfiguration

`Config.BusinessCards` in `config/business.lua`:

```lua
Config.BusinessCards = {
    item = 'business_card',
    command = 'businesscards',   -- opens the print dialog
    amount = 10,                 -- cards per print
    price = 50,                  -- cash per print
    maxTitle = 32,
    maxPhone = 20,
    maxText = 60,
    excludeJobs = { unemployed = true },
    jobs = {
        police = { title = 'LOS SANTOS POLICE DEPARTMENT', header = 'To Protect and to Serve', emblem = 'shield', primary = '#0b1f3a', secondary = '#f5f6f8', accent = '#d4af37' },
    },
    default = { header = 'Los Santos', emblem = 'star', primary = '#2b3440', secondary = '#f6f6f4', accent = '#c8a24a' },
}
```

Ein Job ohne Eintrag in `jobs` bekommt das `default`-Design mit seinem Job-Label als Titel. Jobs in `excludeJobs` können nicht drucken.

<Info>
  Um eine Telefonnummer aus einem anderen Handy-Script zu zeigen, bearbeite `bridge/phone.lua`. Siehe [Telefonnummer](/de/jaksam-identity/server/hooks/phone-number).
</Info>
