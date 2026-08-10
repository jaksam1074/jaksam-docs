---
title: "Installation"
description: "Installiere Billing UI mit ESX oder QBCore auf deinem FiveM-Server."
icon: "download"
---

Die Installation des Scripts ist sehr einfach.

## Voraussetzungen

- **ESX** oder **QBCore**
- Bei ESX muss `esx_billing` entfernt werden (siehe Warnung unten)
- Bei QBCore das [`menu_default`](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing)-Script

<Danger>
  Verwende **KEIN** FileZilla, um die Dateien hochzuladen, sonst funktioniert das Script **NICHT**.

  Verwende stattdessen [WinSCP](https://winscp.net/eng/download.php).
</Danger>

<Tabs>
  <Tab title="ESX">
    <Steps>
      <Step title="Herunterladen und entpacken">
        Lade das Script herunter und entpacke es in deine Resources.
      </Step>
      <Step title="Zum Autostart hinzufügen">
        Füge das Script zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
      <Step title="Datenbank einrichten">
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `billing_ui/sql/` manuell ausführen.
      </Step>
      <Step title="Optionen konfigurieren">
        Konfiguriere die Optionen in den Config-Dateien (lies die Kommentare, sie erklären alles).
      </Step>
    </Steps>

    <Warning>
      Entferne unbedingt `esx_billing`, um Probleme zu vermeiden.
    </Warning>
  </Tab>
  <Tab title="QBCore">
    <Steps>
      <Step title="Herunterladen und entpacken">
        Lade das Script herunter und entpacke es in deine Resources.
      </Step>
      <Step title="Zum Autostart hinzufügen">
        Füge das Script zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
      <Step title="Datenbank einrichten">
        Das Script richtet die Datenbank **automatisch** ein. Falls das nicht klappt, kannst du die Dateien im Ordner `billing_ui/sql/` manuell ausführen.
      </Step>
      <Step title="Optionen konfigurieren">
        Konfiguriere die Optionen in den Config-Dateien (lies die Kommentare, sie erklären alles).
      </Step>
      <Step title="menu_default installieren">
        Lade [menu_default](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) herunter und entpacke es in deine Resources, **ohne es umzubenennen**, und füge es zu deinem Autostart hinzu (Beispiel: `server.cfg`).
      </Step>
    </Steps>
  </Tab>
</Tabs>

Du bist startklar! Viel Spaß mit dem Script 😁

## Verifizierung

<Info>
  [TODO: INFORMATION NEEDED] Für Billing UI ist noch keine Ingame-Prüfung für eine erfolgreiche Installation dokumentiert.
</Info>

## Optionaler Schritt

Nachdem die Datenbank korrekt eingerichtet wurde, kannst du die Dateien im Ordner `billing_ui/sql/` löschen, damit das Script nicht bei jedem Start erneut versucht, die Datenbank einzurichten.
