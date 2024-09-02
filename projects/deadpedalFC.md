---
layout: project
type: project
image: img/deadpedalFC/deadpedal_fc_logo.png
title: "Deadpedal (Faycrest Studios)"
date: September 2023 - Present
published: true
teamSize: 15
labels:
  - Unreal 5
  - UMG UI
  - C++
  - Blueprints
  - Git
  - itch.io
summary: "Deadpedal is a fast pace 3D arcade-style combat racing game currently in development, where twelve racers from around the world are invited to compete in an underground race with one goal in mind, to win."
---

<script type='text/javascript'>
  window.smartlook||(function(d) {
    var o=smartlook=function(){ o.api.push(arguments)},h=d.getElementsByTagName('head')[0];
    var c=d.createElement('script');o.api=new Array();c.async=true;c.type='text/javascript';
    c.charset='utf-8';c.src='https://web-sdk.smartlook.com/recorder.js';h.appendChild(c);
    })(document);
    smartlook('init', '2fb05b8dec724caa0120461df1b0cf9bdc7826d4', { region: 'eu' });
</script>

<main>
  <div class="text-center">
    <div class="ratio ratio-21x9 pb-3">
      <iframe src="https://www.youtube.com/embed/f6xTHd7CBD0?si=ooNljA1lKjgeIscB" title="Deadpedal Progress" allowfullscreen width="800px"></iframe>
    </div>
    
    <div>
      <p class="pt-3 pb-1">Deadpedal is a fast pace 3D arcade-style combat racing game, where twelve racers from around the world are invited to compete in an underground race with one goal in mind, to win.</p>
    </div>
    
    <div class="ratio ratio-21x9 pb-3">
      <iframe src="https://www.youtube.com/embed/f6xTHd7CBD0?si=ooNljA1lKjgeIscB" title="Deadpedal Progress" allowfullscreen width="800px"></iframe>
    </div>

    <h2>Power Ups & Cars:</h2>

    <div>
      <p>
For my programming test when I was first recruited to the studio, I was handed a vehicle framework and a vehicle AI framework and told to make them function together and the rest is history. While my role with them has diminished over time with the AI portion being given to another programmer on the team I have been working with and on the cars since I first started there. 
      </p>
    </div>

    <div class="text-center pb-3">
      <img class="img-fluid" src="../img/deadpedalFC/deadpedal_fc_logo.png" width="800px">
    </div>
    
    <div>
      <p>
When a user clicks an item button, system passes the corresponding car part to a storage object. When you leave the garage the player car pulls and applies the new meshes and materials from the storage object. 
      </p>
    </div>
    
    <h2>UI & Systems:</h2>
    
    <div>
      <p>
The settings menu was designed with the intent to provide the player with a variety of options to help improve their experience. It started out with an interest in trying to provide ways to optimize graphical performance as well as allow the player to rebind controls. The design became oriented primarily around buttons and trying to provide each sub option as a simple click. While this was easy to set up, it took up a lot of space on the screen.
      </p>
    </div>
    
    <div class="text-center pb-3">
      <img class="img-fluid" src="../img/deadpedalFC/deadpedal_fc_logo.png" width="800px">
    </div>
    
    <div>
      <p>
I made a smaller UI widget which allowed the player to push arrow keys to change the settings values, doing this allowed for more options to be displayed and make it easier to keep track of which setting the player is interacting with. In the push for optimization I projected one of Unreals functions, a benchmark test, to the front in the form of a button. When pressed, the benchmark button checks the computer and updates all of the users settings to reflect the results of the test. 
      </p>
    </div>
    
    <div class="text-center pb-3">
      <img class="img-fluid" src="../img/deadpedalFC/deadpedal_fc_logo.png" width="800px">
    </div>

    <h2>Technical Information:</h2> 
    
    <div>
      <p>
Developed in Unreal Engine 5 with Visual Studios and Git
      </p>
    </div>
 </div>
</main>

<hr class="my-4">

itch.io Page: <a href="https://faycrest.itch.io/deadpedal" target="_blank">Click Here</a>
