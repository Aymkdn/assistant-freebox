# assistant-freebox

<div class="important message">CE PLUGIN N'EST PLUS MAINTENU ! MON TEMPS EST MAINTENANT CONSACRÉ À LA VERSION CLOUD QUI PERMET DE FAIRE ENCORE PLUS DANS LE PILOTAGE DE LA FREEBOX : <a href="https://assistant.kodono.info/freebox/">https://assistant.kodono.info/freebox/</a></div>

-----------------------------------------------------------------------------------------------------------------------

Ce plugin de [`assistant-plugins`](https://aymkdn.github.io/assistant-plugins/) permet de contrôler la Freebox Révolution/Delta/One.

> Consulter [le changelog](https://github.com/Aymkdn/assistant-freebox/blob/master/changelog.md) pour connaitre les dernières mises à jour.

**ATTENTION** : vous n'avez besoin **QUE** du plugin `assistant-freebox` pour piloter la Freebox (pas besoin de `assistant-ifttt` ou `assistant-wait`, ou autre....).  
Le seul autre plugin que vous pouvez **ÉVENTUELLEMENT** installer, est le plugin `assistant-notifier`, et **SEULEMENT** dans le cas où vous avez un Google Home chez vous. En effet, si vous utilisez la commande vocale `va dans le dossier ...`, alors un message est envoyé au Google Home pour dire si le dossier a été trouvé ou non. Pour le moment, c'est la seule utilisation du retour vocal vers le Google Home.

<div class="important message">Tu cherches seulement à contrôler la <b>Freebox à la voix, mais sans rien installer ?</b> Alors regarde cet autre projet : <a href="https://assistant.kodono.info/freebox/">https://assistant.kodono.info/freebox/</a></div>

## Sommaire

  - [Installation](#installation)
  - [Configuration](#configuration)
  - [Utilisation](#utilisation)
  - [Personnalisation](#personnalisation)
  - [Commandes](#commandes)
  - [Exemple](#exemple)

## Installation

Si vous n'avez pas installé [`assistant-plugins`](https://aymkdn.github.io/assistant-plugins/), alors il faut le faire, et sélectionner **freebox** comme plugin.

Si vous avez déjà installé [`assistant-plugins`](https://aymkdn.github.io/assistant-plugins/), et que vous souhaitez ajouter ce plugin, alors :
  - Pour Windows, télécharger [`install_freebox.bat`](https://github-proxy.kodono.info/?q=https://raw.githubusercontent.com/Aymkdn/assistant-freebox/master/install_freebox.bat&download=install_freebox.bat) dans le répertoire `assistant-plugins`, puis l'exécuter en double-cliquant dessus.  
  - Pour Linux/MacOS, ouvrir une console dans le répertoire `assistant-plugins` et taper :  
  `npm install assistant-freebox@latest --save --loglevel error && npm run-script postinstall`

## Configuration

<iframe width="560" height="315" src="https://www.youtube.com/embed/g-KuRk0oYSg?rel=0" frameborder="0" allowfullscreen></iframe>
  
**/!\ Attention** : pour que le plugin soit fonctionnel, il faut activer le AirMedia sur la Freebox en allant dans **Réglages** → **Applications** → **AirMedia Video** puis **activer AirMedia**.

Éditer le fichier `configuration.json` du répertoire `assistant-plugins`.

Dans la section concernant le plugin `freebox`, on trouve plusieurs paramètres. **Le seul important qu'il vous faut modifier est `code_telecommande`**.

### Paramètre `code_telecommande`

Allumer la Freebox, aller complètement à gauche dans la section **Réglages**, puis descendre jusqu'à **Système**, puis dans **Informations Freebox Player et Server**.

Dans le premier onglet vous trouverez le **code télécommande réseau**. Inscrire ce nombre dans le fichier de configuration.

### Paramètre `box_to_control`

Par défaut c'est la box dénommée `hd1` qui est pilotée, mais il arrive que ce soit `hd2`.

### Paramètre `search_path`

Une des fonctionnalités est la possibilité de se déplacer dans un dossier de la Freebox qui se trouve dans **"Mes Vidéos"**.

Par exemple, en disant *« OK Google, va dans le dossier Star Trek »*. Il va alors fouiller dans la zone indiquée par `search_path` (qui est `/Disque dur/Vidéos/` qui est `Mes Vidéos` dans le menu de la Freebox).

Il est conseillé de réduire la zone de recherche. Par exemple, supposons que vous voulez seulement rechercher parmi vos séries télé qui sont stockées dans `Perso/Mes Séries/`, alors mettre `/Disque dur/Vidéos/Perso/Mes Séries/`.

**Attention**, `search_path` ne fonctionne qu'avec le **disque dur de la Freebox** (cela ne fonctionne **PAS** avec un disque dur sur le réseau). Pour se déplacer dans un disque dur/répertoire distant (type NAS), il faudra créer sa propre applet IFTTT qui donnera les commandes pour se déplacer jusque dans le dossier en question (du style `freebox_home,right,right,ok,down,ok`). Si besoin d'aide, merci de poster [un nouvel issue](https://github.com/Aymkdn/assistant-plugins/issues).

### Paramètre `use_Mon_Bouquet`

À mettre à `true` si vous souhaitez que le lancement de la télé se fasse dans le menu `Mon Bouquet` (vos chaines favorites) plutôt que dans `Freebox TV`.

### Paramètre `use_Chaines_CANAL`

À mettre à `true` si vous souhaitez que le lancement de la télé se fasse dans le menu `Les chaines CANAL` plutôt que dans `Freebox TV`. En activant ce paramètre, les chaines sont numérotées pour supporter [l'ordre fourni](https://alloforfait.fr/tv/canal/) par Canal et non celui de Free.

### Paramètre `check_player_on`

Celui-ci n'est à ajouter que si vous avez des problèmes lorsque le programme vérifie si la Freebox est allumée. Vérifiez d'abord que AirMedia est bien activé (comme inidqué plus haut sur cette page) et essayez de redémarrer votre box.

Si cela ne fonctionne pas et que le programme continue à ne pas réussir à détecter si la Freebox est allumée ou éteinte, alors vous pouvez ajouter le paramètre `check_player_on` en le mettant à la valeur `false`.

### Paramètre `player_ip`

Si vous utilisez un VPN sur l'ordinateur où tourne `assistant-plugins` alors le controle de la Freebox va échouer. Pour remédier à ce problème vous devez ajouter le paramètre `player_ip` dans le fichier `configuration.json` en y indiquant l'adresse IP du Freebox Player. Pour trouver cette IP vous pouvez [regarder cette vidéo](https://youtu.be/UbUXgn-_zdw).

### Paramètre `server_ip`

Si vous utilisez un VPN sur l'ordinateur où tourne `assistant-plugins` alors le controle de la Freebox pourrait échouer. Si vous avez déjà ajouté le paramètre `player_ip` (ci-dessus), alors vous devez aussi fournir l'IP de la Freebox Serveur dans le fichier `configuration.json`. Par défaut cette IP est **192.168.0.254**.

### Paramètre `player_name`

Si vous avez changé le nom réseau du Freebox Player, vous pouvez utiliser ce paramètre pour le renseigner (voir [ce lien pour plus d'informations](https://github.com/Aymkdn/assistant-plugins/issues/110)).

### Paramètre `delay_default`

Par défaut un délai de 500 millisecondes est appliqué entre chaque envoi de commande vers la Freebox. Pour certains cela pose problème. Il est donc possible de modifier ce délai en ajoutant ce paramètre dans le fichier de configuration.

### Paramètre `delay_canal`

Par défaut un délai de 300 millisecondes est appliqué entre chaque envoi de commande de changement de chaine vers la Freebox (par exemple pour zapper sur la 12, on envoie `1`, on attend 300ms, puis on envoie `2`). Pour certains cela pose problème. Il est donc possible de modifier ce délai en ajoutant ce paramètre dans le fichier de configuration.

### Paramètre `delay_volume`

Par défaut un délai de 20 millisecondes est appliqué entre chaque envoi de commande de volume vers la Freebox (pour augmenter/baisser le volume). Il est possible de modifier ce délai en ajoutant ce paramètre dans le fichier de configuration.

### Paramètre `app_token`

La valeur de ce paramètre est un jeton d'authentification qui est automatiquement généré par la Freebox lors du processus d'autorisation. Il peut parfois s'avérer nécessaire de supprimer `app_token` pour forcer sa recréation lors du prochain démarrage, par exemple si l'on change de Freebox ou si l'on révoque l'accès de l'application `assistant-freebox` depuis Freebox OS.

## Utilisation

Il faut créer une applet IFTTT pour chaque commande vocale. On procède ainsi :

  1. Créer une nouvelle *applet* dans IFTTT : [https://ifttt.com/create](https://ifttt.com/create)  
  2. Cliquer sur **this** puis choisir **Google Assistant** (ou **Amazon Alexa** ou **Cortana**)  
  3. Choisir la carte **Say a simple phrase** (ou autre, selon votre cas)  
  4. Dans *« What do you want to say? »* mettre la phrase qui va déclencher l'action (par exemple **allume la Freebox**)  
  5. Remplir les autres champs de la carte  
  6. Maintenant, cliquer sur **that** puis choisir **Pushbullet**  
  7. Choisir la carte **Push a Note**  
  8. Dans le champs *« Title »*, mettre `Assistant`  
  9. Dans le champs *« Message »*, mettre `freebox_` suivi par la commande souhaitée (si plusieurs commandes, les séparer par une virgule). Par exemple, pour allume la Freebox on aura `freebox_on` (voir les commandes plus bas)  
  10. Enregistrer puis cliquer sur **Finish**  
  11. Dites : « OK Google » (ou le trigger de votre assistant) suivi de votre phrase spéciale du point 4)… Par exemple « OK Google, allume la Freebox » – à noter qu'il faut utiliser le mot-clé **"déclenche"** avec Alexa : « Alexa, déclenche allume la Freebox »  
  12. Votre assistant devrait s'exécuter

### Commandes

Dans l'étape 9) précédente, vous devez y indiquer une commande. Voici donc les commandes disponibles :

  - `red` : touche rouge de la télécommande (envoie la commande `red`)
  - `yellow` : touche jaune de la télécommande (envoie la commande `yellow`)
  - `blue` : touche bleue de la télécommande (envoie la commande `blue`)
  - `green` : touche verte de la télécommande (envoie la commande `green`)
  - `up` : flèche haut (envoie la commande `up`)
  - `down` : flèche bas (envoie la commande `down`)
  - `left` : flèche gauche (envoie la commande `left`)
  - `right` : flèche droite (envoie la commande `right`)
  - `OK` : envoie la commande `OK`
  - `mute` : sourdine (envoie la commande `mute`)
  - `play` : lecture (envoie la commande `play`)
  - `fwd` : avance rapide (envoie la commande `fwd`)
  - `bwd` : retour rapide (envoie la commande `bwd`)
  - `waitXXXX` : enclenche un timer de XXXX millisecondes
  - `on` : allume la Freebox (envoie la séquence `power` suivi d'un timer de 7 secondes (`wait7000`))
  - `off` : envoie la commande `power`
  - `tv` : permet d'aller dans le mode TV
  - `unmute` : coupe/remet le son (envoie `mute`)
  - `home` : envoie la séquence `home`, `wait2000`, `red`
  - `back` : envoie la commande `red`
  - `pause` : envoie la commande `play`
  - `videos` : permet d'aller dans "Mes Vidéos"
  - `photos` : permet d'aller dans "Mes Photos"
  - `musiques` : permet d'aller dans "Mes Musiques"
  - `enregistrements` : permet d'aller dans "Mes enregistrements" (envoie la séquence `home`, `wait2000`, `red`, `up`, `ok`)
  - `direct` : remet le direct (envoie la séquence `green`, `ok`)
  - `soundDown` : baisse le son de 1 point (envoie la commande `vol_dec`)
  - `soundUp` : augmente le son de 1 point (envoie la commande `vol_inc`)
  - `soundLongDown` : baisse le son de 30 points (utile pour ceux qui utilisent des barres de son) (envoie la commande `vol_dec` en simulant un appui long)
  - `soundLongUp` : augmente le son de 30 points (utile pour ceux qui utilisent des barres de son) (envoie la commande `vol_inc` en simulant un appui long)
  - `programUp` : changement de chaine (envoie la commande `prgm_inc`)
  - `programDown` : changement de chaine (envoie la commande `prgm_dec`)
  - `folder XYZ` : permet de chercher le répertoire XYZ dans `search_path` (qui est défini dans la configuration, et qui fonctionne avec "Mes Vidéos"), puis de s'y rendre
     - `folder{/Disque dur/Musiques/} XYZ` : permet de chercher le répertoire XYZ dans `/Disque dur/Musiques` et de s'y rendre (utilisation avec "Mes Musiques")
     - `folder{/Disque dur/Photos/} XYZ` : permet de chercher le répertoire XYZ dans `/Disque dur/Photos` et de s'y rendre (utilisation avec "Mes Photos")
  - `zappe sur ABC` ou `zappe sur la 123` : permet de zapper sur la chaine ABC ou sur la chaine dont le numéro est 123 (exemple : `freebox_zappe sur la 1` ou `freebox_zappe sur TF1`)
  - `zappelong sur ABC` ou `zappelong sur la 123` : permet de zapper sur la chaine ABC ou sur la chaine dont le numéro est 123 en faisant un appui long sur la touche (typiquement cela est utilisé pour le changement de chaine dans "Les Chaines Canal")
  - on peut aussi utiliser `*X` pour effectuer X fois la même action (exemple : `freebox_soundUp*5` équivaut à `freebox_soundUp,soundUp,soundUp,soundUp,soundUp`)

### Exemples

Par exemple, supposons que vous avez un enregistrement journalier (disons l'émission [Quotidien de Yann Barthès qui passe sur TMC](https://www.tf1.fr/tmc/quotidien-avec-yann-barthes)), et que vous souhaitez lancer le dernier Quotidien enregistré.

Pour cela vous souhaitez donner la commande : *OK Google, lance le programme Quotidien*

Il faut donc créer une applet IFTTT (comme décrit plus haut) et pour la commande envoyée à Pushbullet vous mettrez : `freebox_enregistrements,wait7000,ok,ok` qui peut se traduire par `Freebox, va dans Mes Enregistrements, puis patiente 7 secondes, et ensuite appuie sur OK, puis OK encore une fois`

Autre exemple, pour zapper sur une chaine avec Google Assistant : on va créer une applet IFTTT de type **Say a phrase with a text ingredient**. Ensuite, on enverra la commande : `freebox_zappe sur $` (avec `$` qui est le text ingrédient).
