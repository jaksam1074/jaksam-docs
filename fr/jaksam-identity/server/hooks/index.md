---
title: "Hooks"
description: "Fonctions serveur modifiables de Jaksam Identity : permissions, dispatch des descentes, log admin et numéro de téléphone."
icon: "code"
---

Cette page liste les hooks **côté serveur** de Jaksam Identity. Ils se trouvent dans `editable/server.lua` et `bridge/phone.lua`, qui restent ouverts dans la version escrow. Modifie le contenu, mais garde les noms des fonctions et les arguments.

<CardGroup cols={2}>
  <Card title="Peut délivrer" icon="user-check" href="/fr/jaksam-identity/server/hooks/can-issue">
    Décide qui peut délivrer un vrai document.
  </Card>

  <Card title="Peut entrer dans l'atelier" icon="door-open" href="/fr/jaksam-identity/server/hooks/can-enter-workshop">
    Ajoute tes propres conditions pour entrer dans un atelier de faussaire.
  </Card>

  <Card title="Peut faire une descente" icon="building-shield" href="/fr/jaksam-identity/server/hooks/can-raid">
    Ajoute tes propres conditions pour enfoncer la porte d'un atelier.
  </Card>

  <Card title="Pendant une descente" icon="tower-broadcast" href="/fr/jaksam-identity/server/hooks/on-raid">
    Envoie un appel au dispatch ou ta propre alarme quand une descente avance.
  </Card>

  <Card title="À chaque log" icon="clipboard-list" href="/fr/jaksam-identity/server/hooks/on-log">
    Envoie chaque ligne du journal admin vers Discord ou un service de logs.
  </Card>

  <Card title="Numéro de téléphone" icon="phone" href="/fr/jaksam-identity/server/hooks/phone-number">
    Imprime le numéro d'un autre script de téléphone sur les cartes de visite.
  </Card>
</CardGroup>

`Editable.OnIssued` et `Editable.OnForged` reçoivent les mêmes arguments que les events [Document délivré](/fr/jaksam-identity/server/events/document-issued) et [Document falsifié](/fr/jaksam-identity/server/events/document-forged).
