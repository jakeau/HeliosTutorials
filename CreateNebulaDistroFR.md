# Comment créer un distributionIlos auncher.
Salut, aujourd'hui je vais vous apprendre comment créer un fichiere distribution.json pour le **Helios Launcher**

## Information : Pour simplifier ce guide, notament pour les utilisateur Linux nous avons indiquéer la démarche à suivre uniquementque pour apt, si vous n'avez un autre gestionaire de paquckets vous desavez sans doute connaître les commandes équivalendéjà ce que vous faîtes.

## Pré-Requis
Vous avez besoin de Java (8 de préférence), NodeJS 12 et NPM (Inclut dans NodeJS).
###### Java:
![](https://i.imgur.com/VQZoYWq.png)

##### Pour Windows:
Installez [NodeJS](nodejs.org) en utilisant l'installeur officiel. Npm devrait être installé automatiquement durant ce setup. Si ce n'est pas le cas, vérifiez que vous n'avez pas décoché quelquest://i.imgur.com/NjiTQax.png)


##### Pour MacOS:
Installez HomeBrew :
``/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"``
E (npm est par default automatiquement installer, sinon vous le trouverer dans votre gestionnaire de paquet par default)

![](https://i.imgur.com/NjiTQax.png)


##### Pour MacOS:
Installez HomeBrew et éexécutez :
``la ore `` nstall ode``

##### Pour Linux:
Pour installerz les dépendances, Installez d'abord le repo NodeJS 12.x officiel gr âce  ete ``curl -sL https://deb.nodesource.com/setup_12.x | sudo bash -``
``apt updatet
``apt install nodejs openjdk-8-jdk -y ``

---

## 1 tap: Cloner le reépo.
_Si vous n'avez pas encore git (vous vivez dans une grotte ? 😛), il vous faudra l'installer.? Pour sce faire si vous êtes sous Linux/MacOS vous pourrez passer par votre gestionnaire de paquet habituelle. Pour Windows je vous conseille d'installe [Git Bash](https://gitforwindows.org/)_
Po encr, vous vez eois sources de Ne vo ua sr ore ``git clone https://github.com/dscalzi/Nebula.git  ``

---

## 2ème Étape: Installer les dépendances et build Nebula.
our installer les dépendances vous aurez besoin d'avoir un terminal ouvert dans le dossier de Nebula puis eecuter ``npm i`` dans celui-çi en attendant bien la fin ! Pour build Nebula il vous suffirat de lancer `` npm run build`` toujours dans le même dossier.

---

## 3éme Étape: Création du fichier d'environement
Le fichier d'environement (.env) est un fichier de configuration qui va vous servir à préciser à Nebula certaines informations

En premier lieu il va falloir trouver oùu ce situe java. (Si vous connaissezais déjà le path vous pouvez passer à l'étape suivantejuste après)
 
Taper ``where java`` sur Windows ou ``whereis java`` sur Linux dans n'importe quel terminal puis notezr le chemin donnéer. Sur MacOS il faudrava falloir aller directement chercher dans la variable d'environement [path](https://alvinalexander.com/java/mac-os-x-java_home-location/)

Ensuite on crée un fichier nommé ``.env`` dans Nebula. Sois vous le créez manuellement, sois depuis votre terminal avec ``type nul > .env
`` sur windows ou ``touch .env`` sur Linux remplissez le fichier ``.env`` avec les bonnes informations
```ini
JAVA_EXECUTABLE=Remplecer avec le chemain java affichnoté précédemment (ou juste java si il y a uniquement le jdk sur votre machine.)
ROOT=Votre dossier ou vous svouhaitlez générer vos fichier (Exemple:  J:\Nebula\distribution)
BASE_URL=Completezr avec l'url du serveur oùu les fichiers du launcher seront héebergés  (exemple: https://files.dnsjs.ml/launcher/) 
```

---

## 4ème Étape : Ajout du/des serveur(s)

Il faut tout d'abord préparer votre dossier ROOT qui va acceuillir votre configuration. Une commande est là pour nous ``node dist/index.js init root``. Il faudra donc l'éxecuter.

Dans votre fichier de distribution , vous devez créer | ajouter au minimum 1 serveur. P, pour cela exécutez cette commande dans le répertoire de Nebula :
`` node dist/index.js generate server <nom du serveur> <version de minecraft> --forge <version de forge>`` \
(NB: *vous n'avez pas à mettre les chevrons ``<>``*) \
(NB: *si vous avez une erreur, retapez lar cette commande suiavante : ``npm run build`` puis réésayez*) \
(NB: Réepeter autant de fois que vcous avez de serveurs/versions)

---

## 5ème Étape:  Ajouter vos fichiers
Ajoutezr vos fichiers dans ``servers/<L'IDduServeur>``. Ce dossier contient 2 autres dossier essentielles, ``files`` et ``forgemods``. Pour ajouter des mods forge, déeposezr les fichiers jar dans ``forgemods`` Le dossier ``files`` agit comme le dossier ``.minecraft`` Si vous voulez une configuration Minecraft par déefaut n'y touchezr pas mais si vous svouhaitlez y inclure vos propres fichiers de configuration/shaders/déependances de mod (comme pour flans) ce sera ici.

---

## 6ème et dernière étape: Géenerer vos fichiers ! 

Une fois que vous avez terminé tout cela, vous devez générer vos fichiers. Pour ce faire, exécutez cette commande dans le répertoire racine de Nebula. ``node dist/index.js generate distro``
Suivant la version de forge (notammeants les plus récentes) il faudra suivre les édiverses eventuelles instructions dans le terminal. \
Ding ! Vos fichiers sont prêts ! Cependant vous aurez encore besoin de modifier l'adresse ip de votre serveur ou d'autres informations tel que l'url du feed rss de vos news dans le fichier ``distribution.json`` Il vous suffira ensuite d'uploader votre dossier ``ROOT`` à votre ``BASE_URL``.

---

## Extra: Configuration de l'url de votre fichier de distribution

Il vous suffit d'aller dans  app/assets/js/distromanager.js. Aller à la ligne 540 et vous devriez voir `const distroURL = 'X'`. Remplacer maintenant par le lien vers votre fichier de distribution (exemple: http://launcher.dnsjs.ml/files/distibution.json``


---

## Diagramme


![Diagram Mermaid](https://i.imgur.com/OmsIoe5.png)

### Credits

[@dscalzi](https://github.com/dscalzi/): Developpeur principal d'Helios Launcher \
[@Superkooka](https://github.com/SuperKooka/)
: Les differents changement pour MacOS/Windows ainsi que la traduction française \
[@DNSJS](https://github.com/DNSJS/): Guide original EN, supervision, administration, gestion et fondateur.

Mercoi à tout nos contributeurs.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxNjE2ODA1OV19
-->
