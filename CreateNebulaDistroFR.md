# Comment créer une distribution.json pour Helios Launcher.
Salut, aujourd'hui je vais vous apprendre comment créer une distribution.json pour ces applications:
- **Helios Launcher**

## Exigences
Vous avez besoin de Java, NodeJS et NPM.-
###### Java:
![](https://i.imgur.com/VQZoYWq.png)

##### Pour Windows:
Installez NodeJS en utilisant l'installeur officiel (nodejs.org)

![](https://i.imgur.com/NjiTQax.png)


##### Pour MacOS:
Installez HomeBrew et exécutez:
``brew install node``


##### Pour Linux:
Pour installez les programmes, exécutez ces commandes dans un terminal:
``apt install nodejs default-jdk npm -y ``

---

## 1ère Étape: Cloner le répo.
Pour commencer, vous avez besoin d'avoir Nebula sur votre machine:
``git clone https://github.com/dscalzi/Nebula.git  ``
Linux)
(NB pour les utilisateurs linux: si vous avez pas Git exécutez cette commande:  **``apt install git``**)
(NB pour les utilisateurs windows: si vous avez pas encore Git installez Git Bash)
Windows)
(NB pour les utilisateurs MacOS :si vous avez pas encore Git installez le en utilisant Homebrew  (``brew install git``)

---

## Deuxième Étape: Installer les dépendances et build Nebula.
Pour installer les dépendances vous aurez besoin d'avoir un terminal ouvert dans le dossier de Nebula puis executer ``npm i`` dans celui-çi en atendant bien la fin ! Pour build Nebula il vous suffirat de lancer `` npm run build`` toujours dans le même dossier.

---

## 3éme Étape: Création du fichier d'environement
Le fichier d'environement est un fichier de configuration qui va vous servir à préciser à Nebula certaines informations

En premier lieu il va falloir trouver ou ce situe java. (Si vous connaisais déjà le path vous pouvez passer à l'étape juste après)

Sur Windows et Linux : 
Taper ``where java`` sur Windows ou ``whereis java`` sur Linux dans n'importe quel terminal puis noter le chemin donner.

Sur MacOS :
C'est un petit peu compliquer car il vous faudra chercher dans le path à la main : [PATHS](https://alvinalexander.com/java/mac-os-x-java_home-location/)
```ini
JAVA_EXECUTABLE=Fill in with the Java PATH
ROOT=Votre dossier ou vous voulez générer vos fichier (courament distribution)
BASE_URL=Completer avec l'url du serveur ou les fichiers du launcher seront hebergés  (exemple: files .dnsjs.ml/launcher) 
```

---

## 4ème Étape

Dans voyee fichier de distribution , vous devez créer ajouter au minimum 1 serveur, pour cela exécutez cette commande dans le répertoire de Nebula :
`` node dist/index.js generate server <nom du serveur> <version de minecraft> --forge <version de forge>``
(Note: *vous n'avez pas à mettre les chevrons <>*)
(Note x2: *si vous avez une erreur, retaper cette commande avant ``npm run build``*)

---

## 5ème Étape:  Ajouter vos fichiers
Ajouter vos fichiers dans ``servers/<YourServerID>``. Ce dossier en contiens 2 essentiels, files et forgemods.
Pour ajouter des mods forge, deposer les fichiers jar dans ``forgemods``
Le dossier ``files`` agit comme le dossier ``.minecraft`` Si vous voulez un configuration Minecraft par defaut n'y toucher pas mais si vous voulez y inclure vos propres fichiers de configuration/shaders/dependance de mod (comme pour flans) ce sera ici.

---

## 6ème et dernière étape: Generer vos fichiers ! 

Une fois que vous avez terminé tout cela, vous devez générer vos fichiers.
Pour ce faire, exécutez cette commande dans le répertoire racine de Nebula.
`generate distro`
Suivant la version de forge (notamants les plus récentes) il faudra suivre les diverses instruction dans le terminal.
Ding ! Vos fichiers sont pret ! Cependant vous aurez encore besoin de modifier l'adresse ip de votre serveur ou d'autre information tel que l'url du feed rss de vos news dans le fichier ``distribution.json`` Il vous suffira ensuite d'uploader votre dossier ``ROOT`` à votre ``BASE_URL``.

---

## Extra: Comment configurer l'url de votre fichier de distribution modifier

Il vous suffit d'aller dans  app/assets/js/distromanager.js. Aller à la ligne 540 et vous devriez voir `const distroURL = 'X'`. Remplacer maintenant par le lien vers votre fichier de distribution (exemple: launcher.dnsjs.ml/files/distibution.json``


---

## Diagramme


![Diagram Mermaid](https://i.imgur.com/OmsIoe5.png)

### Credits

@dscalzi: Developpeur principal d'Helios Launcher
@Superkooka: Les differents changement pour MacOS/Windows ainsi que la traduction française
Le 11/04/2020 est mon anniversaire !
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzU3MTg5ODQ0LDk1MDA2MTc0NV19
-->
