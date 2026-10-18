---
title: "RoadPhone-Wallet"
description: "Zeige die Dokumente, die ein Spieler trägt, in der RoadPhone-Wallet oder in jedem anderen Handy-Script."
icon: "mobile-screen"
---

Wenn dein RoadPhone den Wallet-Modus `jksm_identity` hat, setze in der `config.lua` von RoadPhone:

```lua
Config.Wallet = {
    Mode = 'jksm_identity',
    IdentityResource = 'jksm_identity',
    -- ...
}
```

Die Wallet listet dann die Dokumente, die der Spieler trägt, mit Foto und gedruckten Daten. Eines zu zeigen, öffnet die 3D-Karte für den anderen Spieler.

## Was die Wallet listet

Wie eine echte Brieftasche nur, was der Spieler tatsächlich bei sich hat:

- das Hauptinventar
- die Container in `Config.WalletContainers` (Standard `{ 'wallet' }`), keine ID-Stapel

Ein gefälschtes oder gestohlenes Dokument zeigt, was darauf gedruckt ist: Das Register wird nie gefragt.

<Info>
  - **ox_inventory:** Eine Brieftasche zählt nur, wenn sie ein ox-Container ist (`setContainerProperties`) und in `Config.WalletContainers` steht.
  - **qb-inventory:** Es hat keine Container, die Wallet liest also nur das Hauptinventar.
</Info>

## Andere Handy-Scripts

Andere Handy-Scripts können dasselbe mit zwei Server-Exports tun:

- [Wallet-Dokumente abrufen](/de/jaksam-identity/server/wallet/get-wallet-documents): die Dokumente, die der Spieler trägt, als Kartendaten
- [Dokument zeigen](/de/jaksam-identity/server/wallet/show-document): zeigt einem Spieler in der Nähe ein mitgeführtes Dokument als 3D-Karte
