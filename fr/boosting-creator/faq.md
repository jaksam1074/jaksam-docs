---
title: "FAQ"
description: "Questions fréquemment posées spécifiques à Boosting Creator : offres qui n'arrivent jamais, voitures qui n'apparaissent pas, l'item du laptop, les traceurs, vehicles_keys et les garages."
icon: "circle-question"
---

Cette page contient des FAQ liées **UNIQUEMENT à ce script**. Pense à consulter aussi la [FAQ commune](/fr/jaksams-scripts/common-faq) pour les autres problèmes.

<AccordionGroup>
  <Accordion title="Je suis dans la file mais aucune offre n'arrive">
    Une offre a besoin d'une classe débloquée par le joueur qui a aussi :

    - au moins un véhicule
    - assez de policiers en ligne (le réglage **Policiers en service requis** de la classe)
    - une zone de recherche libre et une livraison libre pour cette classe

    Avec les réglages par défaut, la première offre arrive après 45 à 120 secondes. Regarde l'onglet **En direct** : un joueur en cooldown ou à la limite journalière est listé sous **Joueurs en attente**.
  </Accordion>

  <Accordion title="Le contrat est annulé quand je m'approche de la voiture">
    La voiture est créée par le jeu du joueur et vérifiée par le serveur. Si la console du serveur affiche `wasn't created, is the model valid?` :

    - le modèle de la classe est faux, ou une voiture addon n'est pas streamée
    - `sv_entityLockdown` est réglé sur `strict`, donc les joueurs ne peuvent pas créer d'entités
  </Accordion>

  <Accordion title="Utiliser le laptop ne fait rien">
    L'item n'existe probablement pas dans ton inventaire : la console du serveur l'indique au démarrage, en jaune. Crée-le comme indiqué dans [Item du laptop](/fr/boosting-creator/installation#item-du-laptop). Si tu as renommé l'item dans les paramètres, redémarre le script.
  </Accordion>

  <Accordion title="Les policiers ne peuvent pas rejoindre la file">
    C'est voulu : les jobs de `POLICE_JOBS_NAMES` ne peuvent pas faire de boosting. Voir [Police](/fr/boosting-creator/guides/police).
  </Accordion>

  <Accordion title="La police ne voit pas le traceur">
    Les pings vont uniquement aux jobs de `POLICE_JOBS_NAMES` (`integrations/sh_integrations.lua`). Ajoute-y les noms de tes jobs de police et redémarre le script.
  </Accordion>

  <Accordion title="Les mini-jeux d'effraction et de démarrage aux fils n'apparaissent pas">
    Avec `vehicles_keys` démarré, la voiture est crochetée et démarrée aux fils avec vehicles_keys, et l'effraction et le démarrage aux fils du script ne sont pas utilisés. C'est voulu.
  </Accordion>

  <Accordion title="Pourquoi je ne peux pas ranger cette voiture dans mon garage ?">
    Seuls les contrats de livraison simples peuvent être rangés : pas les contrats VIN scratch ou de casse, pas les voitures pour lesquelles un fixer a demandé quelque chose, et pas quand le garage a déjà 6 voitures.
  </Accordion>

  <Accordion title="Le porte-voitures ne peut pas partir">
    Le panneau à l'intérieur du garage indique pourquoi. Il faut au moins le nombre de voitures réglé dans **Voitures requises pour tout vendre**, assez de policiers en service, et un acheteur en gros libre à au moins 2 500 m du garage (par défaut).
  </Accordion>

  <Accordion title="Je ne peux pas supprimer un garage">
    Des joueurs le possèdent. Reprends-le d'abord à chacun d'eux dans l'onglet **Joueurs**.
  </Accordion>

  <Accordion title="La livraison a été refusée car trop rapide">
    Une voiture qui arrive plus vite que n'importe quel vrai trajet (par exemple après une téléportation) est refusée, et la tentative est loguée sur Discord.
  </Accordion>
</AccordionGroup>
