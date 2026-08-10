---
title: "Häufige Fragen"
description: "Häufig gestellte Fragen für alle Scripts"
icon: "circle-user-circle-question"
---

Diese Seite enthält häufige Fragen, die für alle Scripts gelten. Falls dein Problem hier nicht aufgeführt ist, sieh in der FAQ des jeweiligen Scripts nach, mit dem du Probleme hast.

<AccordionGroup>
  <Accordion title="Absturz">
    Abstürze können 2 Ursachen haben:

    - Du musst diese Objektmodelle in deinem Anticheat whitelisten: `L1_1`, `GetHashKey('L1_1')`, `2116969379`
    - Falls du nach dem Whitelisten dieser Objektmodelle in deinem Anticheat weiterhin Abstürze hast, sieh dir [diese Seite](/de/jaksams-scripts/troubleshooting) an

    _Falls du nicht weißt, wie du Objektmodelle in deinem Anticheat whitelistest, frag den Ersteller deines Anticheats._
  </Accordion>

  <Accordion title="Attempted to index a nil value (field 'ESX')">
    Wenn du diesen Fehler hast, bedeutet das, dass das Script das Shared Object von ESX nicht abrufen konnte.

    Dieser Fehler kann durch andere Fehler in deiner Server-/F8-Konsole verursacht werden, die vorher auftreten.

    Falls du keinen anderen Fehler davor hast, sieh dir [diese Seite](/de/jaksams-scripts/troubleshooting) an.
  </Accordion>

  <Accordion title='Fehler "missing menu_default" beheben'>
    Um den Fehler zu beheben, lies einfach die Installationsanleitung des Scripts.
  </Accordion>

  <Accordion title="Objekte/Props spawnen nicht">
    Falls die Props nicht spawnen, liegt es höchstwahrscheinlich an deinem Anticheat.

    Achte darauf, alle Props in deinem Anticheat zu whitelisten. Falls du nicht weißt wie, frag den Ersteller deines Anticheats.
  </Accordion>

  <Accordion title="Kann KEIN Item erhalten">
    Falls du es bereits mit verschiedenen Items versucht hast und keines davon erhältst, sieh dir [diese Seite](/de/jaksams-scripts/troubleshooting) an.
  </Accordion>

  <Accordion title="Kann NUR WAFFEN nicht erhalten">
    Falls nur Waffen Probleme verursachen, Items aber funktionieren, sind das die möglichen Gründe:

    - Bei ESX liegt es höchstwahrscheinlich daran, dass dein Server die Standard-ESX-Methode `xPlayer.addWeapon` nicht unterstützt
    - Bei QBCore kann es sein, dass dein Inventar das Standardverhalten von `qb-inventory` verändert

    Das ist kein Problem, das vom Script abhängt, sondern von deinem Framework/Inventar, und kann nicht von uns gelöst werden — die Standardmethoden müssen funktionieren.
  </Accordion>

  <Accordion title="Wie man Standard-Benachrichtigungen ersetzt">
    Um die Benachrichtigungen eines beliebigen Scripts zu ersetzen, sieh in der Dokumentation des Scripts nach. Es gibt Events, mit denen du die Standard-Benachrichtigung deaktivieren und eine externe aufrufen kannst.

    _Hinweis: Die Integration externer Scripts liegt komplett bei dir._
  </Accordion>

  <Accordion title="Wie man die Standard-Progress-Bar ersetzt">
    Um die Progress-Bar eines beliebigen Scripts zu ersetzen, sieh in der Dokumentation des Scripts nach. Es gibt Events, mit denen du die Standard-Progress-Bar deaktivieren und eine externe aufrufen kannst.

    _Hinweis: Die Integration externer Scripts liegt komplett bei dir._
  </Accordion>

  <Accordion title="Script-Transfers">
    Scripts können nur einmal über den FiveM Keymaster übertragen werden, indem du den seitlichen Button statt "Download" verwendest. Es gibt in keinem Fall manuelle Widerrufe oder manuelle Transfers.
  </Accordion>

  <Accordion title="Rückerstattungen">
    Käufe in jaksam's Store sind endgültig, das gilt für jede Situation — falsches Framework, falscher Account usw. Bei Rückerstattungen können wir daher leider überhaupt nicht helfen.
  </Accordion>
</AccordionGroup>
