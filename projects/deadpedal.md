---
layout: project
type: project
image: img/deadpedal/deadpedal_logo.png
title: "Dead Pedal"
date: August 2022 - May 2023
published: true
teamSize: 23
labels:
  - Unreal 5
  - UMG UI
  - C++
  - Git
  - Steam
  - itch.io
summary: "Dead Pedal is a 3rd person, action, open world driving game set in a fictional version of the Mojave desert."
---

<script type='text/javascript'>
  window.smartlook||(function(d) {
    var o=smartlook=function(){ o.api.push(arguments)},h=d.getElementsByTagName('head')[0];
    var c=d.createElement('script');o.api=new Array();c.async=true;c.type='text/javascript';
    c.charset='utf-8';c.src='https://web-sdk.smartlook.com/recorder.js';h.appendChild(c);
    })(document);
    smartlook('init', '2fb05b8dec724caa0120461df1b0cf9bdc7826d4', { region: 'eu' });
</script>

<div class="ratio ratio-21x9">
  <iframe src="https://www.youtube.com/embed/hmdd7PEL4Rg" title="Dead Pedal Trailer" allowfullscreen width="800px"></iframe>
</div>

<p class="pt-3 pb-1">Dead Pedal is a 3rd person, action, open world driving game set in a fictional version of the Mojave desert, where your goal is to cause as much chaos and destruction as possible. Go out and explore the world's threats to get revenge for your fallen goldfish, Ted. 
  
<div class="ratio ratio-21x9">
  <iframe src="https://www.youtube.com/embed/meNLQpxT9xs" title="Garage Video" allowfullscreen width="800px"></iframe>
</div>

<h2>Garage:</h2>

When the garage is first loaded in it generates menu tabs and item buttons based on data tables. The menu creates new item buttons as needed when switching tabs, and make any buttons that aren't needed by a tab unseen and not intractable by the player until the player goes to a tab that needs them. Each data table (Pictured below) contains the values which correspond to each button including: item name, item ID, static mesh, material instance, locked status, etc. The data tables are designed to be easily modified by other members of the team, so the system is not dependent on me for adding new customization options. 

 <div class="text-center">
   <img class="img-fluid" src="../img/deadpedal/dpDataTable.PNG" width="800px">
 </div>

When a user clicks an item button, system passes the corresponding car part to a storage object. When you leave the garage the player car pulls and applies the new meshes and materials from the storage object. 

<h2>Settings Menu:</h2>
 
The settings menu was designed with the intent to provide the player with a variety of options to help improve their experience. It started out with an interest in trying to provide ways to optimize graphical performance as well as allow the player to rebind controls. The design became oriented primarily around buttons and trying to provide each sub option as a simple click. While this was easy to set up, it took up a lot of space on the screen.

  <div class="text-center">
   <img class="img-fluid" src="../img/deadpedal/dpSettingsMenu_old.PNG" width="800px">
 </div>
 
I made a smaller UI widget which allowed the player to push arrow keys to change the settings values, doing this allowed for more options to be displayed and make it easier to keep track of which setting the player is interacting with. In the push for optimization I projected one of Unreals functions, a benchmark test, to the front in the form of a button. When pressed, the benchmark button checks the computer and updates all of the users settings to reflect the results of the test. 
 
 <div class="text-center">
   <img class="img-fluid" src="../img/deadpedal/dpSettingsMenu.png" width="800px">
 </div>

<h2>Technical Information:</h2> 

Developed in UE5 and Visual Studios

</p>

<hr class="my-4">

Steam Page: <a href="https://store.steampowered.com/app/2250160/Dead_Pedal/">Click Here</a>

itch.io Page: <a href="https://larnio.itch.io/dead-pedal">Click Here</a>
