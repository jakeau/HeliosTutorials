# How to create a distribution.json for Helios Launcher.

Hey, today I'm gonna tell you how to create a distribution.json for the following applications:
- **Helios Launcher**

## Requirements
You need to have NodeJS, Java and npm:
###### Java:
![](https://i.imgur.com/VQZoYWq.png)

##### For Windows:
Install NodeJS using the legacy installer (nodejs.org)

![](https://i.imgur.com/NjiTQax.png)


##### For MacOS:
Install HomeBrew and run: 
``brew install node``
Then sit back and relax x)

##### For Linux:
To install them type:
``apt install nodejs default-jdk npm -y ``


## 1st step: Clone the repository.


To begin, you need to clone the Nebula repository.
``git clone https://github.com/dscalzi/Nebula.git  ``

Linux)
(Note: if you don't have git then do **``apt install git``**)

Windows)
(Note: if you don't have git then install Git Bash)

## 2nd step: Install Dependencies and Build Nebula.
To install dependencies, you need to execute ``npm i``  in the repository's directory.
and to build Nebula, simply execute ``npm build ./ `` and `` npm run build`` in the same directory. 


## 3rd step:   .env Creation
Windows)
Type ``where java`` and execute it. Then note the given PATH.

Linux)
Execute ``whereis java`` and note the given PATH.
To make Nebula work properly, you need to create a file that is named .env 
Once you've created it type in this. You will need to fill it.

MacOS)
It's a little bit more difficult, you need to see if any of these paths belongs to your Java installation: [PATHS](https://alvinalexander.com/java/mac-os-x-java_home-location/)
```
JAVA_EXECUTABLE=Fill in with the Java PATH
ROOT=Somewhere
BASE_URL=Fill in with the URL that you want to have your files on (exemple: files .dnsjs.ml/launcher) 
```

## 4th step: Create a server

To create a modded distribution.json (distro.json), you need to create a modded server. To do that, run this command while in the Nebula directory:
`` node dist/index.js generate server <ServerName> <MCServerVersion> --forge <ForgeSpecificVersion>``

(Note: *you don't have to type the brackets <>*)

(Note x2: *if you receive an error try doing ``npm run build``*)

(Note x3: You can use `latest` or `recommended` as a value for the forge version.
It will resolve the corresponding version, if it exists)

## 5th step:  Put in your files 
To start putting in your mods, go to ``servers/<YourServerID>``.
Go to ``forgemods``, and put in  your mods (*try to have no special characters in your mods' name*). 
##### Optional: Put your flans mod, in the flans folder and if there is some mods that require folders in the minecraft root directory, put them in there.

## 6th and last step: Creating the distribution.json.

Once you've finished all of this, you actually need to create the distribution.json file.
Todo so, execute this command while in Nebula's root directory.
`node dist/index.js generate distro`
Then you will get your distribution.json ready. You just need to put the new folders that Nebula generated in a webserver at the base url that you've specified in the .env.

## Extra: How to Configure Your Distribution.json URL In Helios Launcher

Now that all of your files are ready, just go to app/assets/js/distromanager.js. Go to line 540 or nearby and you should see `const distroURL = 'X'` replace it with `const distroURL = 'YourDistroURL (example: launcher.dnsjs.ml/files/distibution.json)'`


## Diagram


![Diagram Mermaid](https://i.imgur.com/OmsIoe5.png)
### Credits: 
@dscalzi: for Nebula and Helios Launcher.
@SuperZooka: for figuring out how to run it on Windows/MacOS
The 11/04/2020 is my birthday.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ3OTExNDk4MF19
-->
