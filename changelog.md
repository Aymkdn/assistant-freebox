# Changelog

**Change Log v2.0.15 (15 septembre 2019)**

  - Suppression de l'utilisation du HTTPS pour les personnes en mode bridge (voir https://github.com/Aymkdn/assistant-plugins/issues/254)

**Change Log v2.0.14 (14 septembre 2019)**

  - Prend en compte le paramètre `check_player_on` (voir https://github.com/Aymkdn/assistant-plugins/issues/254)

**Change Log v2.0.13 (18 août 2019)**

  - Ajout des chaines optionnelles (voir https://github.com/Aymkdn/assistant-freebox/issues/22)

**Change Log v2.0.12 (4 mars 2018)**

  - Ajout des commandes `musiques` et `photos`, ainsi qu'une option supplémentaire pour la commande `folder` (voir https://github.com/Aymkdn/assistant-freebox/issues/18)
  - Ajout des commandes `soundLongUp` et `soundLongDown` (voir https://github.com/Aymkdn/assistant-freebox/issues/19) pour ceux qui utilisent une barre de son

**Change Log v2.0.11 (1 décembre 2018)**

  - Ajout de la commande `zappelong` (voir https://github.com/Aymkdn/assistant-plugins/issues/194)

**Change Log v2.0.10 (29 août 2018)**

  - Ajout du paramètre `server_ip` qui permet d'indiquer l'IP de son Freebox Server dans le cas de l'utilisation d'un VPN (voir https://github.com/Aymkdn/assistant-plugins/issues/169)

**Change Log v2.0.9 (8 avril 2018)**

  - Ajout du support de la chaine Mosaïque (0) (voir https://github.com/Aymkdn/assistant-plugins/issues/124)

**Change Log v2.0.8 (1 avril 2018)**

  - Ajout du paramètre `player_name` pour ceux qui changent le nom de leur Freebox Player (voir https://github.com/Aymkdn/assistant-plugins/issues/110)

**Change Log v2.0.7 (21 janvier 2018)**

  - Correction d'un bug introduit dans la v2.0.6

**Change Log v2.0.6 (21 janvier 2018)**

  - La commande `off` vérifie désormais que la Freebox est allumée avant d'essayer de l'éteindre
  - Mise en cache des chaines TV pour éviter de les récupérer à chaque démarrage du programme

**Change Log v2.0.5 (3 Janvier 2018)**

  - Ajout du paramètre `player_ip` qui permet d'indiquer l'IP de sa Freebox Player dans le cas de l'utilisation d'un VPN
  - Passage à la v4 du protocol de la Freebox Server

**Change Log v2.0.4 (2 Janvier 2018)**

  - Les chaines Canal sont maintenant supportées en utilisant le paramètre `use_Chaines_CANAL`
  - Simplification des commandes envoyées pour revenir à la home (on passe de 3 commandes à 1 seule)

**Change Log v2.0.3 (12 Décembre 2017)**

  - Il est maintenant possible de configurer le délai entre les commandes envoyées vers la Freebox

**Change Log v2.0.1 (2 Décembre 2017)**

  - Correction d'un bug avec le paramètre `check_player_on`

**Change Log v2.0.1 (2 Décembre 2017)**

  - Amélioration des messages d'erreur

**Change Log v2.0 (30 Novembre 2017)**

  - Le plugin devient autonome avec une nouvelle structure pour le programme

**Change Log v1.1 (22 Novembre 2017)**

  - Délai passé à 3 secondes après la touche `home` (car 2 secondes n'étaient parfois pas suffisants)
  - Changement de l'enregistrement de la configuration pour le support des système Linux (merci à @LudoMeurillon)
  - Lors de la recherche d'un dossier, s'il n'est pas trouvé, Google Home va l'indiquer par un message "le dossier n'a pas été trouvé"
  - Si le code télécommande est incorrecte, le programme va maintenant retourner une erreur

**Change Log v1.0 (19 Novembre 2017)**

  - Première release publique
