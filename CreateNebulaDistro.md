# How to create a distribution.json for Helios Launcher.

Hey, today im gonna tell you how to create a distribution.json for the following applications:
- **Helios Launcher**

## Requirements

You can easily create a **distribution.json** , but you need a Linux Machine as:

- A *VPS*
- A Linux *Computer*
- A *virtual machine*


And if you don't have a Linux Machine, well you can follow this step-by-step guide to create a Virtual Linux Machine.
- [Guide](https://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox)

You also need Java, npm and NodeJS:
To install them type:
``apt install nodejs default-jdk npm -y ``

## 1st step: Clone the repository.


To create a modded distribution.json (distro.json), you need to clone the Nebula repository.
``git clone https://github.com/dscalzi/Nebula.git  ``
(Note: if you don't have git then do **``apt install git``**)
Theb 
## 2st step: Install Dependencies.
To install dependencies, you need to execute ``npm i``  in the repository's directory.


## 3st step:   .env Creation

Execute ``whereis java`` and note the given PATH.
To make Nebula work properly, you need to create a file that is named .env 
Once you've created it type in this. You will need to fill it.
```
JAVA_EXECUTABLE=Fill in with the Java PATH
ROOT=Somewhere
BASE_URL=Fill in with the URL that you want to have your files on (exemple: files .dnsjs.ml/launcher) 
```

## 4st step: Create a server

### Forge:
To create a modded distribution.json (distro.json), you need to create a modded server, to do that: run this command while in the nebula directory:
`` generate server <ServerName> <MCServerVersion> --forge <ForgeSpecificVersion>``
(Note: *you don't have to type the brackets <>*)
### Vanilla:
Well it's a little bit different that the Forge server. You've only got to remove the --forge
So you need to execute this command while in the nebula directory:
`` generate server <ServerName> <MCServerVersion>``
## Optional: Put in your files (forge)
To start putting in your mods, go to ``servers/<YourServerID>``.
Go to ``forgemods``, and put in  your mods (*try to have no special characters in your mods' name*). 
##### Optional: Put your flans mod, in the flans folder and if there is some mods that require folders in the minecraft root directory, put them in there.

## 5st and last step: Creating the distribution.json.

Once you've finished all of this, you actually need to create the distribution.json file.
Todo so, execute this command while in Nebula's root directory.
`generate distro`
Then you will get your distribution.json ready. You just need to put the new folders that Nebula generated in a webserver at the base url that you've specified in the .env.
## Extra: How to Configure Your Distribution.json URL In Helios Launcher

Now that all of your files are ready, just go to app/assets/js/distromanager.js. Go to line 540 or nearby and you should see `const distroURL = 'X'` replace it with `const distroURL = 'YourDistroURL (example: launcher.dnsjs.ml/files/distibution.json)'`


## Diagram


![Diagram Mermaid](https://i.imgur.com/OmsIoe5.png)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwOTMxMzAwMiw3MzI3NjA1ODNdfQ==
-->