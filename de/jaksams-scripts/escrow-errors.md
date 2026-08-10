---
title: "Escrow-Fehler"
description: "Lösungen für häufige Fehler durch das FiveM-Asset-Escrow-System"
icon: "lock-hashtag"
---

<Danger>
  Wenn die Scripts funktionieren und nach ein paar Server-Neustarts aufhören zu funktionieren, hast du einen Virus auf deinem Server. In diesem Fall können wir nicht helfen.
</Danger>

Hier findest du Lösungen für häufige Fehler bei der Nutzung von jaksam's Scripts, die durch das FiveM-Escrow-System verursacht werden.

Um zu prüfen, ob dein Fehler durch das FiveM-Asset-Escrow verursacht wird, starte einfach das Script neu und prüfe **sowohl** die **F8-Konsole** als auch die **Serverkonsole** (txAdmin) auf Fehler.

## Wie erkenne ich, ob mein Fehler durch das FiveM-Escrow-System verursacht wird?

Um zu verstehen, ob etwas in einem Script wegen des FiveM-Asset-Escrow-Systems nicht funktioniert, geh so vor:

<Steps>
  <Step title="Script neu starten">
    Starte das Script, das Probleme verursacht, neu, mit dem Befehl `ensure dein_script_name` in der txAdmin-Konsole oder auf deine gewohnte Weise.

    <Frame caption="Beispiel: F8-Neustart im Spiel">
      ![in-game F8 restart example](/images/f8_restart.gif)
    </Frame>

    <Frame caption="Beispiel: Neustart über die Serverkonsole">
      ![server console restart example](/images/server_restart.gif)
    </Frame>
  </Step>
  <Step title="Beide Konsolen prüfen">
    Prüfe **sowohl** die txAdmin-Konsole (Serverkonsole) **als auch** die F8-Konsole im Spiel auf Fehler.
  </Step>
  <Step title="Mit bekannten Fehlern vergleichen">
    Falls ein Fehler den Beispielen unten ähnelt, **wird dein Problem durch das FiveM-Asset-Escrow-System verursacht**.
  </Step>
</Steps>

### Beispiele für Fehler durch das FiveM-Escrow-System

<Frame caption="Lösung: siehe Error parsing script unten">
  ![Escrow error example](/images/error_parsing.png)
</Frame>

<Frame caption="Lösung: siehe Error parsing script unten">
  ![Escrow error example](/images/error_parsing_2.png)
</Frame>

<Frame caption="Lösung: siehe Failed to verify protected resource unten">
  ![Escrow error example](/images/failed_to_verify_protected_resource.png)
</Frame>

<Frame caption="Lösung: siehe You lack the required entitlement unten">
  ![Escrow error example](/images/lack_entitlement.jpg)
</Frame>

## Häufige Ursachen

Das sind die häufigsten Ursachen bei **allen** Escrow-Fehlern unten, prüfe diese zuerst, bevor du dich mit den fehlerspezifischen Abschnitten befasst:

- Du überträgst die Script-Datei einzeln auf deinen VPS, anstatt die **.zip** hochzuladen und sie **nachdem** sie schon auf dem VPS ist, zu entpacken
- Du verwendest **FileZilla** (oder dein Hoster tut es) — verwende stattdessen [WinSCP](https://winscp.net/eng/download.php)
- Der Download war beschädigt — versuch eine saubere Neuinstallation
- Du hast einen Virus auf deinem Server, der Script-Dateien verändert (sehr wahrscheinlich, wenn nichts anderes hilft)

Weitere allgemeine Anforderungen:

- **Mindestens** Server-Artifacts-Version 4752
- OneSync muss aktiviert sein
- Verwende den richtigen Lizenzschlüssel, generiert vom selben Account, mit dem du das Script heruntergeladen hast

<Tip>
  Es wird **dringend** empfohlen, alle Abschnitte unten sorgfältig zu lesen, da diese Lösungen von vielen Nutzern getestet wurden und funktionieren sollten. Falls nichts davon hilft, siehe [Was tun, wenn nichts die Fehler behebt](#was-tun-wenn-nichts-die-fehler-behebt).
</Tip>

Alle Scripts von jaksam findest du [hier](https://jaksam1074-fivem-scripts.tebex.io/).

<AccordionGroup>
  <Accordion title="Error parsing script ... <\1>">
    Beispiel-Fehlermeldung:

    ```text
    Error parsing script @jobs_creator/server/markers/job_shop.lua in resource jobs_creator: @jobs_creator/server/markers/job_shop.lua:1: syntax error near '<\1>'
    ```

    ### Mögliche Gründe

    Zusätzlich zu den [häufigen Ursachen](#haufige-ursachen) oben kann dieser Fehler auch auftreten, wenn:

    - Du eventuell die **Server**-Caches leeren musst

    ### Wie prüfe ich meine Serverversion?

    Um zu prüfen, welche Serverversion dein Server aktuell verwendet, nutze folgenden Befehl in deiner FiveM-Serverkonsole: `version`

    **Beispiel**

    <Frame>
      ![version command example](/images/version_example.jpg)
    </Frame>

    ### Wie aktualisiere ich meine Serverversion?

    Um deine Serverversion zu aktualisieren, lade die neuen [Server-Artifacts](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/) herunter und ersetze sie in deinem Serverordner.

    Das ist die **offizielle** [FiveM-Anleitung](https://docs.fivem.net/docs/server-manual/setting-up-a-server/) zur Aktualisierung deines Servers.

    ### Meine Serverversion ist bereits aktuell, aber ich habe trotzdem den Fehler

    Falls du den Fehler trotz aktueller Serverversion hast, sieh dir [Failed to verify protected resource](#failed-to-verify-protected-resource) unten an.
  </Accordion>

  <Accordion title="Failed to verify protected resource">
    Beispiel-Fehlermeldung:

    ```text
    [svadhesive] Failed to verify protected resource jobs_creator
    ```

    ### Mögliche Gründe

    Zusätzlich zu den [häufigen Ursachen](#haufige-ursachen) oben kann dieser Fehler auch auftreten, wenn:

    - Du keine `.fxap`-Datei im Script-Ordner hast

    ### Lösungen

    <Steps>
      <Step title="Script erneut herunterladen">
        Lade das Script erneut vom [FiveM Portal](https://portal.cfx.re/) herunter.
      </Step>
      <Step title="Mit WinSCP hochladen">
        Lade das Script mit [WinSCP](https://winscp.net/eng/download.php) hoch, _nicht_ mit FileZilla.
      </Step>
      <Step title="Server neu starten">
        Starte den Server neu.
      </Step>
    </Steps>
  </Accordion>

  <Accordion title="You lack the required entitlement">
    Beispiel-Fehlermeldung:

    ```text
    You lack the required entitlement to use script_name
    ```

    ### Grund

    Alle Scripts, die das FiveM-Escrow-System verwenden, sind an deinen FiveM-Account gebunden (den Account, den du auf Tebex verwendet hast).

    Damit sie funktionieren, benötigen die Scripts einen Server mit einem Serverschlüssel, der vom selben FiveM-Account erstellt wurde, den du auf Tebex verwendet hast.

    ### Was ist ein Serverschlüssel?

    - Der Serverschlüssel wird im [FiveM Portal](https://portal.cfx.re/) generiert
    - Der Serverschlüssel ist **kein** Scriptschlüssel
    - Ein FiveM-Server kann nur **1** Serverschlüssel verwenden

    **Beispiel eines Serverschlüssels in server.cfg**

    ```text
    sv_licenseKey "27ztq5g2pcjua67q4xywujkuzh5m7j4a"
    ```

    ### Wie prüfe ich meinen Serverschlüssel?

    Um zu prüfen, welchen Serverschlüssel dein Server aktuell verwendet, nutze folgenden Befehl in deiner FiveM-Serverkonsole: `sv_licenseKey`

    **Beispiel:**

    <Frame>
      ![sv\_licenseKey example](/images/example_server_key.jpg)
    </Frame>

    ### Wie prüfe ich, ob ich den richtigen Serverschlüssel verwende?

    <Steps>
      <Step title="Deinen Serverschlüssel holen">
        Nutze den Befehl `sv_licenseKey` in deiner FiveM-Serverkonsole.
      </Step>
      <Step title="Serverschlüssel notieren">
        Notiere dir den **Serverschlüssel**, den du aktuell verwendest.
      </Step>
      <Step title="FiveM Keymaster öffnen">
        Gehe zum [FiveM Portal](https://portal.cfx.re/).
      </Step>
      <Step title="Script-Besitz prüfen">
        Prüfe, ob der Account, mit dem du im [FiveM Portal](https://portal.cfx.re/) eingeloggt bist, die Scripts besitzt, die du verwenden möchtest. Falls das Script dort nicht auftaucht, hast du auf Tebex einen anderen Account verwendet oder das Script auf einen anderen Account übertragen.

        **Beispiel mit dem** [**Jobs-Creator-Script**](https://forum.cfx.re/t/jobs-creator-4-6-esx-in-game-job-creation-menu-without-server-restart/2667762)

        <Frame>
          ![Jobs Creator ownership example](/images/example_purchased_assets.jpg)
        </Frame>
      </Step>
      <Step title="Besitzer des Serverschlüssels prüfen">
        Falls der Account, den du im [FiveM Portal](https://portal.cfx.re/) verwendest, die Scripts besitzt, prüfe, ob der **Serverschlüssel** deines Servers vom selben Account generiert wurde.

        <Frame>
          ![Server key owner example](/images/keymaster_keys_list.jpg)
        </Frame>
      </Step>
    </Steps>

    ### Mein Serverschlüssel wurde von jemand anderem generiert, was kann ich tun?

    Du hast 2 Möglichkeiten:

    - Einen Schlüssel von deinem eigenen Account generieren und verwenden
    - Den Script-Besitz auf den anderen Account übertragen

    ### Wie übertrage ich das Script auf einen anderen Account?

    Um das Script auf einen anderen Account zu übertragen, gehe zu:

    [FiveM Portal](https://portal.cfx.re/) → **Assets**-Tab → **Transfer to another account** (roter Button)

    <Warning>
      cfx.re hat entschieden, dass Scripts nur 1 Mal übertragen werden können, du kannst das Script also danach nicht erneut übertragen.
    </Warning>

    ### ZAP-Hosting-Serverschlüssel

    Falls du einen Zap-Hosting-Server verwendest, musst du deinen Serverschlüssel **nicht** in server.cfg eintragen, sondern direkt auf deren Website.

    [Hier ist die offizielle ZAP-Hosting-Anleitung dafür](https://zap-hosting.com/guides/docs/en/fivem_licensekey/).

    **Beispiel-Screenshot:**

    <Frame>
      ![ZAP Hosting license key example](/images/zap_hosting_custom_key.png)
    </Frame>
  </Accordion>

  <Accordion title="Was tun, wenn nichts die Fehler behebt">
    ### Ich habe alle Schritte befolgt, aber nichts funktioniert, was kann ich tun?

    Falls du alle Schritte befolgt hast, hast du einfach einen Virus auf deinem Server. Versuche, einen sauberen Server nur mit den Standard-Framework-Scripts und den Scripts von jaksam zu erstellen.

    ### Wie prüfe ich, ob ich einen Virus auf meinem Server habe?

    Öffne die vom Script von jaksam genannte Datei mit **Notepad** und scrolle zum Ende. Falls dort teilweise lesbarer Code steht (zum Beispiel `local...`), ist das ein Virus, der von etwas anderem hinzugefügt wurde, denn normalerweise wäre die gesamte Datei verschlüsselt. In diesem Fall musst du dieses Problem lösen, bevor du irgendein Script verwenden kannst.
  </Accordion>
</AccordionGroup>
