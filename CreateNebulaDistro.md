---


---

<h1 id="how-to-create-a-distribution.json-for-helios-launcher.How to create a distribution.json for Helios Launcher.</h1>
<p>

Hey, today im gonna tell you how to create a distribution.json for the following applications:</p>
<ul>
<li><strong>Helios Launcher</strong></li>
</ul>
<h2 id="requirements">Requirements</h2>
<p>You can easily create a <strong>**distribution.json</strong> , but you need a Linux Machine as:</p>
<ul>
<li>A <em>VPS</em></li>
<li>A Linux em>*Computer</em></li>
<li>A <em>virtual machine</em></li>
</ul>
<p>And if you don’t have a Linux Machine, well you can follow this step-by-step guide to create a Virtual Linux Machine.</p>
<ul>
<li><a href="https://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox">Guide</a></li>
</ul>
<p>You also need Java, npm and NodeJS:<br>To install them type:<br>
<code>apt install nodejs default-jdk npm -y</code></p>
<h2 id="st-step-clone-the-repository.">1st step: Clone the repository.</h2>
<p>To create a modded distribution.json (distro.json), you need to clone the Nebula repository.<br>
<code>git clone https://github.com/dscalzi/Nebula.git</code><br>
(Note: if you don’t have git then do <strong><code>apt install git</code></strong>)<br>
Theb</p>
<h2 id="st-step-install-dependencies-and-build-the-repository.">2st step: Install Dependencies and Build the repository.</h2>
<p>
To install dependencies, you need to execute <code>npm i</code>  in the repository’s directory.<br>
To build it, run <code>``npm build</code></p>
<h2 id="st-step---.env-creation">``
 3st step:   .env Creation</h2>
<p>

Execute <code>``whereis java</code> and note the given PATH.<br>
To make Nebula work properly, you need to create a file that is named .env<br>
Once you’ve created it type in this. You will need to fill it.</p>
<pre><code>
```
JAVA_EXECUTABLE=Fill in with the Java PATH
ROOT=Somewhere
BASE_URL=Fill in with the URL that you want to have your files on (exemple: files .dnsjs.ml/launcher) 
</code></pre>
<h2 id="st-step-create-a-server">4st step: Create a server</h2>
<h3 id="forge">Forge:</h3>
<p>To create a modded distribution.json (distro.json), you need to create a modded server, to do that: run this command while in the nebula directory:<br>
<code>generate server &lt;ServerName&gt; &lt;MCServerVersion&gt; --forge &lt;ForgeSpecificVersion&gt;</code><br>
(Note: em>*you don't have to type the brackets &lt;&gt;</em>)</p>
<h3 id="vanilla">Vanilla:</h3>
<p>Well it’s a little bit different that the Forge server. You’ve only got to remove the --forge<br>
So you need to execute this command while in the nebula directory:<br>
<code>generate server &lt;ServerName&gt; &lt;MCServerVersion&gt;</code></p>
<h2 id="optional-put-in-your-files-forge">Optional: Put in your files (forge)</h2>
<p>
To start putting in your mods, go to <code>servers/lt;<YourServerID&gt;</code>.<br>
Go to ode>``forgemods</code>, and put in  your mods (<em>try to have no special characters in your mods’' name</em>).</p>
<h5 id="optional-put-your-flans-mod-in-the-flans-folder-and-if-there-is-some-mods-that-require-folders-in-the-minecraft-root-directory-put-them-in-th Optional: Put your flans mod, in the flans folder and if there is some mods that require folders in the minecraft root directory, put them in there.</h5>
<h2 id="st-and-last-step-creating-the-distribution.json.">5st and last step: Creating the distribution.json.</h2>
<p>Once you've finished all of this, you actually need to create the distribution.json file.<br>
Todo so, execute this command while in Nebula’s root directory.<br>
<code>generate distro</code><br>
Then you will get your distribution.json ready. You just need to put the new folders that Nebula generated in a webserver at the base url that you’ve specified in the .env.</p>
<h2 id="extra-how-to-configure-your-distribution.json-url-in-helios-launcher">Extra: How to Configure Your Distribution.json URL In Helios Launcher</h2>
<p>Now that all of your files are ready, just go to app/assets/js/distromanager.js. Go to line 540 or nearby and you should see code>`const distroURL = 'X'</code>` replace it with code>`const distroURL = 'YourDistroURL (example: launcher.dnsjs.ml/files/distibution.json)'</code></p>
<h2 id="diagram![Diagram</h2>
<p><img src=" Mermaid](https://i.imgur.com/OmsIoe5.png" alt="Diagram"></p>
)
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzMyNzYwNTgzXX0=
-->