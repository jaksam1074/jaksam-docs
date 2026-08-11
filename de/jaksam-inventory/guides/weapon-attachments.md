---
title: "Waffen-Anbauteile"
icon: "gun"
description: "Mehrere Waffen-Komponenten-IDs auf ein einzelnes Anbauteil-Item abbilden"
---

## Warum es diese Anleitung gibt

In GTA V hat jede Waffe unterschiedliche Komponenten-IDs für den gleichen Anbauteil-Typ. Zum Beispiel:

- Ein Schalldämpfer für eine Pistole nutzt `COMPONENT_AT_PI_SUPP`
- Ein Schalldämpfer für eine Combat Pistol nutzt `COMPONENT_AT_PI_SUPP_02`

**Das Inventarsystem vereinfacht das:** Du kannst EIN Item erstellen (wie "Schalldämpfer"), das automatisch mit allen kompatiblen Waffen funktioniert, indem du mehrere Komponenten-IDs darauf abbildest.

## Schritt-für-Schritt-Anleitung

### Schritt 1: Prüfen, ob das Item existiert

Prüfe zuerst, ob bereits ein Item für deinen Anbauteil-Typ in deiner Datenbank existiert.

<Tabs>
  <Tab title="Standard-GTA-Waffen">
    - Die häufigsten Anbauteile (Schalldämpfer, Extended Clip, Taschenlampe usw.) sollten schon existieren
    - Nutze den `/inventory`-Befehl im Spiel, um bestehende Items zu prüfen
  </Tab>
  <Tab title="Modifizierte Waffen">
    - Du musst entweder ein neues Item erstellen ODER den Komponenten-Hash der modifizierten Waffe zu einem bestehenden Item hinzufügen
    - Beispiel: Falls du eine modifizierte AK47 mit Schalldämpfer hast, kannst du deren Schalldämpfer-Hash zum bestehenden "Schalldämpfer"-Item hinzufügen
  </Tab>
</Tabs>

**Item erstellen/bearbeiten:**

<Steps>
  <Step title="Inventar-Verwaltungs-UI öffnen">
    Gib `/inventory` im Spiel ein.
  </Step>
  <Step title="Ein Item erstellen oder bearbeiten">
    Erstelle ein neues Item oder bearbeite ein bestehendes.
  </Step>
  <Step title="Den richtigen Item-Typ setzen">
    <CardGroup cols={2}>
      <Card title="barrel">
        Schalldämpfer, Mündungsbremsen
      </Card>

      <Card title="clip">
        Magazine
      </Card>

      <Card title="scope">
        Visiere und Optiken
      </Card>

      <Card title="flashlight">
        Taktische Lichter
      </Card>

      <Card title="grip">
        Vordergriffe
      </Card>
    </CardGroup>

    <Frame caption="Beispiel mit Standard-Schalldämpfer">
      ![Edit default suppressor item component example](/images/weapon-attachments-item-example.jpg)
    </Frame>
  </Step>
</Steps>

### Schritt 2: Komponenten-Hashes hinzufügen

Jetzt musst du die Komponenten-Hash(es) hinzufügen, für die dieses Item bei Waffen gelten soll.

**Wo man Komponenten-Hashes findet:**

<Tabs>
  <Tab title="Standard-GTA-Waffen">
    - Sieh im [Wiki](https://docs.fivem.net/docs/game-references/weapon-models/) nach
    - Oder suche online nach "GTA V weapon components list"
  </Tab>
  <Tab title="Modifizierte Waffen">
    - Höchstwahrscheinlich enthält dein Waffen-Mod-Script eine Textdatei mit den Komponenten-Hashes
    - Ein Beispiel für Komponentennamen: sie beginnen oft mit `COMPONENT_`
    - Kontaktiere den Ersteller der Waffe/die Dokumentation, falls du es nicht findest
  </Tab>
</Tabs>

**Wie man sie hinzufügt:**

<Steps>
  <Step title="Component-Hashes-Bereich öffnen">
    Finde im Item-Bearbeitungsbildschirm des Anbauteil-Items den Bereich "Component Hashes".
  </Step>
  <Step title="Einen Hash hinzufügen">
    Klicke auf "Add Component Hash".
  </Step>
  <Step title="Den Hash eingeben">
    Gib den Komponenten-Hash ein (z.B. `COMPONENT_AT_PI_SUPP`).
  </Step>
  <Step title="Wiederholen">
    Wiederhole das für alle Komponenten, mit denen dieses Anbauteil funktionieren soll.
  </Step>
</Steps>

<Info>
  Das Menü zeigt dir, welche Waffen mit jedem hinzugefügten Komponenten-Hash kompatibel sind.
</Info>

<Frame caption="Beispiel für die Liste der Item-Hashes">
  ![Edit item hashes list example](/images/weapon-attachments-hashes-example.jpg)
</Frame>

### Schritt 3: Im Spiel testen

<Steps>
  <Step title="Gib dir selbst das Item">
    `/giveitem [deine_id] [item_name] 1` oder über das Omnipack (`F1` bei geöffnetem Inventar).
  </Step>
  <Step title="Gib dir selbst eine Waffe">
    Gib dir eine kompatible Waffe.
  </Step>
  <Step title="Anbringen">
    Versuche, die Komponente anzubringen.
  </Step>
</Steps>

<Tip>
  Das war's! Das System wendet automatisch die richtige Komponente basierend auf der Waffe an.
</Tip>

## Vollständiges Beispiel

Angenommen du willst einen Schalldämpfer für eine modifizierte Waffe namens "WEAPON_MODDEDAK47" hinzufügen:

<Steps>
  <Step title="Bestehende Items prüfen">
    Öffne `/inventory` und suche nach "Schalldämpfer", er existiert!
  </Step>
  <Step title="Das Item bearbeiten">
    Klicke auf "Bearbeiten" beim Schalldämpfer-Item.
  </Step>
  <Step title="Den Hash hinzufügen">
    Füge `COMPONENT_MODDEDAK47_SUPP` zur Liste der Komponenten-Hashes hinzu.
  </Step>
  <Step title="Speichern">
    Speichere das Item.
  </Step>
  <Step title="Testen">
    Gib dir den Schalldämpfer und die modifizierte AK47 und versuche, ihn anzubringen.
  </Step>
</Steps>
