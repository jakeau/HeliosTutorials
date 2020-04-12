# Comment créer une distribution.json pour Helios Launcher.
Salut, aujourd'hui je vais vous apprendre comment créer une distribution.json pour ces applications:
- **Helios Launcher**

## Information : Pour simplifier ce guide, notament pour les utilisateur Linux nous avons indiquer la démarche à suivre que pour apt, si vous n'avez un autre gestionaire de packet vous savez déjà ce que vous faîtes

## Pré-Requis
Vous avez besoin de Java, NodeJS et NPM.

###### Java:
![](https://i.imgur.com/VQZoYWq.png)

##### Pour Windows:
Installez [NodeJS](nodejs.org) en utilisant l'installeur officiel (npm est par default automatiquement installer, sinon vous le trouverer dans votre gestionnaire de paquet par default)

![](https://i.imgur.com/NjiTQax.png)


##### Pour MacOS:
Installez HomeBrew et exécutez:
``brew install node``


##### Pour Linux:
Pour installez les programmes, exécutez ces commandes dans un terminal:
``apt install nodejs default-jdk npm -y ``

---

## 1ère Étape: Cloner le répo.
_Si vous n'avez pas encore git (vous vivez dans une grotte ? 😛), il vous faudra l'installer? Pour ce faire si vous êtes sous Linux/MacOS vous pourez passer par votre gestionnaire de paquet habituelle. Pour Windows je vous conseille d'installer [Git Bash](https://gitforwindows.org/)_

Pour commencer, vous avez besoin d'avoir les sources de Nebula sur votre machine:
``git clone https://github.com/dscalzi/Nebula.git  ``

---

## 2ème Étape: Installer les dépendances et build Nebula.
Pour installer les dépendances vous aurez besoin d'avoir un terminal ouvert dans le dossier de Nebula puis executer ``npm i`` dans celui-çi en atendant bien la fin ! Pour build Nebula il vous suffirat de lancer `` npm run build`` toujours dans le même dossier.

---

## 3éme Étape: Création du fichier d'environement
Le fichier d'environement est un fichier de configuration qui va vous servir à préciser à Nebula certaines informations

En premier lieu il va falloir trouver ou ce situe java. (Si vous connaisais déjà le path vous pouvez passer à l'étape juste après)
 
Taper ``where java`` sur Windows ou ``whereis java`` sur Linux dans n'importe quel terminal puis noter le chemin donner. Sur MacOS il va falloir aller directement chercher dans la variable d'environement [path](https://alvinalexander.com/java/mac-os-x-java_home-location/)

Ensuite remplissez le fichier ``.env`` avec les bonnes informations
```ini
JAVA_EXECUTABLE=Remplecer avec le chemain noté précédement
ROOT=Votre dossier ou vous voulez générer vos fichier (Exemple:  J:\Nebula\distribution)
BASE_URL=Completer avec l'url du serveur ou les fichiers du launcher seront hebergés  (exemple: http://files.dnsjs.ml/launcher/) 
```

---

## 4ème Étape : Ajout du/des serveur(s)

Dans votre fichier de distribution , vous devez créer ajouter au minimum 1 serveur, pour cela exécutez cette commande dans le répertoire de Nebula :
`` node dist/index.js generate server <nom du serveur> <version de minecraft> --forge <version de forge>`` \
(NB: *vous n'avez pas à mettre les chevrons ``<>``*) \
(NB: *si vous avez une erreur, retaper cette commande avant ``npm run build``*) \
(NB: Repeter autant de fois que cous avez de serveurs/versions)

---

## 5ème Étape:  Ajouter vos fichiers
Ajouter vos fichiers dans ``servers/<L'IDduServeur>``. Ce dossier contient 2 autres dossier essentielles, ``files`` et ``forgemods``. Pour ajouter des mods forge, deposer les fichiers jar dans ``forgemods`` Le dossier ``files`` agit comme le dossier ``.minecraft`` Si vous voulez un configuration Minecraft par defaut n'y toucher pas mais si vous voulez y inclure vos propres fichiers de configuration/shaders/dependance de mod (comme pour flans) ce sera ici.

---

## 6ème et dernière étape: Generer vos fichiers ! 

Une fois que vous avez terminé tout cela, vous devez générer vos fichiers. Pour ce faire, exécutez cette commande dans le répertoire racine de Nebula. `generate distro` \
Suivant la version de forge (notamants les plus récentes) il faudra suivre les diverses eventuelles instructions dans le terminal. \
Ding ! Vos fichiers sont pret ! Cependant vous aurez encore besoin de modifier l'adresse ip de votre serveur ou d'autre information tel que l'url du feed rss de vos news dans le fichier ``distribution.json`` Il vous suffira ensuite d'uploader votre dossier ``ROOT`` à votre ``BASE_URL``.

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
