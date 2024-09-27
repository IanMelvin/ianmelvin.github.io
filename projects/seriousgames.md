---
layout: project
type: project
image: img/seriousgames/segslogo.png
title: "Serious Games (@ UVM)"
date: January 2023 - Present
year: 2023.1 - 2024
published: true
teamSize: 5 - 7
labels:
  - Unity
  - C#
  - Visual Studios
  - Git
summary: "Develop WebGL games that are used to gather data on how people respond to various situations, like flooding and farm management."
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
  <div>
    <div style="max-width: 700px; margin: 1vw auto;">	  
      <div class="text-center" style="position: relative; padding-bottom: 57%; height: 0px;">
        <iframe src="https://www.youtube.com/embed/f6xTHd7CBD0?si=ooNljA1lKjgeIscB" title="Deadpedal Demo" allowfullscreen style="position: absolute; top: 0px; left: 0px; width: 100%; height: 99%;" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"></iframe>
      </div>
    </div>	    
    <div>
      <p class="text-left pt-3 pb-1 fs-5">
						  At UVM, serious games are short, browser based games that are designed to place the user in various situations reflecting the real world. These situations include, a town potentially about to undergo a severe flood, a network of farms exposed to swine flu, and managing a farm. Each of these games produce data based on how the user interacts with the game and adapts to the situations put in front of them. The data produced is handed over to the team researchers who turn the data into a paper based on the intended purpose of the game. The games are developed in a collaborative environment between developers and researchers.</p>
    </div>
    <h2 class="text-center my-4 fs-1">User Interface</h2>
    <hr class="my-4">
    <div class="text-center pb-3">
      <img class="img-fluid" src="../img/deadpedalFC/deadpedal_fc_logo.png" width="700px">
    </div>
    <div>
      <p class="text-left pb-1 fs-5">
						  No matter what type of serious game I'm developing, the UI is always the most important piece of the game. The UI is what conveys the rules of
this world to the player, it's how the player makes their choices and it's what gives the player an idea of how well they're doing. Due to the size 
of the teams for these project being very small, I take on the role of both UI Programmer and UI Designer, in uncommon cases I serve as the UI 
Artist as well. At its core, I try to keep the UI simple and reduce distractions while working with the researchers on the team to make sure what 
is presented is clear and concise, one of the main ways we do this is by breaking down blocks of text into images with brief summaries. If I can 
replace text with a clear and effective visual element, I do.
      </p>
    </div>
    <h2 class="text-center my-4 fs-1">WebGL & Performance</h2>
    <hr class="my-4">
    <div class="text-center pb-3">
      <img class="img-fluid" src="../img/deadpedalFC/deadpedal_fc_logo.png" width="700px">
    </div>
    <div>
      <p class="text-left pb-1 fs-5">
						  One of the big challenges with developing these games comes from the limitation inherent to Unity's WebGL capabilities and the server's that are used 
to host the game when it's up for people to play. During the ongoing development of a game about a town flooding, the team wanted realistic looking 3D 
water going across terrain based on a Vermont town. After a lot of research and prototyping, I determined the best solution would be to create a fluid 
simulation in blender on a replica of the Vermont-inspired town being built in Unity and play it in engine. The fluid simulation would be played as an 
Alembic Animation, we ran into some problems with this, the first one being that the alembic file type isn't supported by Unity's WebGL. In an attempt 
to fix it we moved to recording the flood in Unity and playing the video during run time, Unity WebGL has issues with playing videos stored in the project 
so I set up the project to stream the videos which were being stored in a public git repo. While this generally worked for playing the videos, it was 
inconsistent and left many testers with just the UI overlaying a gray screen. Our current and final solution to this problem came from realizing that we 
could export each individual frame of the fluid simulation as fbx files and build a class to "play" the animation by changing which objects were visible 
in the scene. To cut build size, I lowered the quality of the frames in blender and cut out every other to cutting out 2/3 frames, while this made the 
animation look a little choppy in some area it allowed for an overall better product and with other visual effects in the scene helped to mask these 
imperfections.<br><br>
							  Performance issues are not just a fluid simulation issue, and while most of the serious games I work on don't need major optimization to run effectively, the flood game has continued to need optimization efforts as we expand it's features to include an active intersection and a social media feed. I work with 
the profiler and researched various techniques to reduce memory and cpu load, with many being as simple as removing print to console lines left over from 
testing done by the team. Many of these optimizations ended up being targeted at the UI, while not a major drag on performance, there was room to make to 
lower its memory and cpu usage by reducing what UI elements could be interacted with by removing raycast targeting.
      </p>
    </div>
    <h2 class="text-center my-4 fs-1">Tools</h2> 
    <hr class="my-4">
    <div class="text-center">
      <p>
        {% for label in page.labels %}
        <span style="background-color: var(--tf-pill-bg)" class="badge rounded-pill fs-5">{{ label }}</span>
        {% endfor %}
      </p>
    </div>
 </div>
</main>
