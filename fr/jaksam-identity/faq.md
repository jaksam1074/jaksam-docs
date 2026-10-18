---
title: "FAQ"
description: "Questions fréquemment posées spécifiques à Jaksam Identity, couvrant les ateliers, les descentes, les documents, les sceaux de qb-inventory et les intégrations."
icon: "circle-question"
---

Cette page contient des FAQ liées **UNIQUEMENT à ce script**. Pense à consulter aussi la [FAQ commune](/fr/jaksams-scripts/common-faq) pour les autres problèmes.

<AccordionGroup>
  <Accordion title="Je ne trouve aucun atelier de faussaire dans le monde">
    Aucun atelier n'est configuré de base, tout le côté contrefaçon reste donc invisible tant que tu n'en ajoutes pas un.

    Ajoute-les dans `Config.Forgery.workshops` (`config/forgery.lua`), ou en jeu sur la page des ateliers de `/documents config`. Voir [Ateliers de faussaires](/fr/jaksam-identity/guides/forgery-workshops).
  </Accordion>

  <Accordion title="L'intérieur de l'atelier est vide ou invisible">
    L'atelier utilise l'intérieur des faux papiers des bikers de `bob74_ipl`. Vérifie que `bob74_ipl` est installé et démarre **avant** `jksm_identity`. S'il manque, la console l'indique en rouge au démarrage.
  </Accordion>

  <Accordion title="Les agents ne peuvent rien saisir pendant une descente">
    Chaque unité a besoin d'une salle des scellés. Place-la sur la page des descentes de `/documents config`, ou mets `locker` dans `Config.Raid.forces`. Sans salle des scellés, rien ne peut être saisi.
  </Accordion>

  <Accordion title="Les agents ou les invités dans un atelier ne voient pas les postes">
    C'est voulu. Seuls les membres du job propriétaire voient et utilisent les postes, ordinateurs et portables. Les agents ont leurs propres options pendant une descente : saisir aux étagères et sur le portable du patron, mettre sous scellés à la porte.
  </Accordion>

  <Accordion title="Deux cartes d'identité s'ouvrent en même temps (Qbox)">
    `qbx_idcard` tourne encore. Retire-le : Jaksam Identity répond à sa place, donc les items de départ de qbx_core et qbx_cityhall continuent de fonctionner sans changement.
  </Accordion>

  <Accordion title="Les actions du clic droit View, Show et Copy number manquent (jaksam_inventory)">
    Copie `install/jaksam_item_types.lua` vers `jaksam_inventory_data/_data/jksm_identity.lua` et redémarre `jaksam_inventory` une fois. Voir [Installation](/fr/jaksam-identity/installation#installer-les-items).
  </Accordion>

  <Accordion title="Les documents n'affichent rien et disent que le sceau n'est pas valide (qb-inventory)">
    qb-inventory reprend les données d'un item depuis le client, chaque document porte donc un sceau fait avec une clé que seul le serveur connaît, gardée dans la table `jksm_identity_settings`.

    Si tu as déplacé ou réinitialisé la base sans cette table, la clé a changé et les documents existants ont perdu leur sceau. Restaure la table depuis ta sauvegarde, ou délivre à nouveau les documents.
  </Accordion>

  <Accordion title="La carte d'identité de départ n'a pas de photo">
    C'est voulu. Les documents de départ sont délivrés juste après le chargement du personnage, sans photo. La photo se prend dans une [mairie](/fr/jaksam-identity/guides/citizen-offices) lors d'un renouvellement.
  </Accordion>

  <Accordion title="Les documents achetés en boutique sont détectés comme faux">
    Un document venant d'une boutique ou d'un don d'admin est enregistré (authentique), sauf si sa `rarity` jaksam est listée dans `Config.UnregisteredRarities` (par défaut `illegal`). Change la rareté de l'item, ou retire cette rareté de la liste.
  </Accordion>

  <Accordion title="Les documents expirés ou suspendus fonctionnent encore">
    C'est voulu : **des faits, pas de la contrainte**. L'expiration, les suspensions et les vieilles photos s'affichent sur la carte et au contrôle du registre, mais rien n'est retiré, bloqué ou renouvelé automatiquement. La suite, c'est du roleplay.
  </Accordion>

  <Accordion title="La police peut-elle savoir qui a fait un faux ?">
    Non. Le contrôle du registre ne montre que ce qu'une autorité saurait : aucune fiche, statut, expiration, licences manquantes, données qui ne correspondent pas. Qui l'a fait et sa qualité ne sont visibles que par les admins avec `/documents truth <serial>`. Qui a réellement présenté un document est écrit dans `jksm_identity_log`, pour les admins uniquement.
  </Accordion>

  <Accordion title="Comment ajouter un autre document ou une autre licence ?">
    Ajoute l'item à ton inventaire, puis une entrée dans `Config.Documents` (`config/documents.lua`). Toute licence connue de ton framework peut devenir un document. Voir [Ajouter ton propre document](/fr/jaksam-identity/guides/documents-and-register#ajouter-ton-propre-document).
  </Accordion>

  <Accordion title="Comment changer la langue ou en ajouter une ?">
    `Config.Locale` choisit la langue (`en` et `de` sont fournies), et les admins peuvent la changer en jeu dans `/documents config`. Pour ajouter une langue, copie `locales/en.lua` vers `locales/<code>.lua`, remplace `Locales['en']` par `Locales['<code>']`, traduis les textes et mets le code dans `Config.Locale`. Les clés manquantes retombent sur l'anglais.
  </Accordion>

  <Accordion title="Comment utiliser mes propres notifications, barre de progression ou mini-jeu ?">
    - Notifications : `bridge/notify.lua`, voir [Notifications](/fr/jaksam-identity/client/replace-notifications)
    - Barre de progression : `Editable.Progress` dans `editable/client.lua`, voir [Barre de progression](/fr/jaksam-identity/client/progress-bar)
    - Mini-jeu : `Editable.SkillCheck` dans `editable/client.lua`, voir [Skill check](/fr/jaksam-identity/client/skill-check)
  </Accordion>

  <Accordion title="esx_dmvschool est-il sûr avec ce script ?">
    L'event `esx_dmvschool:addLicense` d'esx_dmvschool n'est pas vérifié côté serveur, un client tricheur peut donc s'attribuer n'importe quelle licence avec. Jaksam Identity fait confiance aux licences de la base. Sécurise cet event dans esx_dmvschool, ou mets `Config.DmvSchool.enabled = false`, sur un serveur en production.
  </Accordion>
</AccordionGroup>
