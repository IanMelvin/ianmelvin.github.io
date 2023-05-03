---
layout: essay
type: essay
title: "My attempt at making Pac-Man clone Pt.1: A* Pathfinding"
# All dates must be YYYY-MM-DD format!
date: 2023-05-03
published: true
labels:
  - Game Programming
  - A*
  - AI
---

In the fall semester of 2022, I recreated the classic arcade game, Pac-Man, in Unity 2D. This project had 2 main caveats, I needed to create the AI using A* pathfinding and the maze needed to have parts of it generated randomly every time the game was run. This post will go over the general process of development for the game, my implementation of A*, and the ups and downs I encountered.

<div class="text-center pb-3">
      <img class="img-fluid" src="../img/Puckle/Puckle_GamePlay.PNG" width="800px">
</div>

## The Basics

Before I can get into any of the fancy talk with A*, I want to talk about what these systems were built on / to work with: the core gameplay elements. As many of you might be familiar with, Pac-Man is a game where you as the player navigate a maze from a top down perspective.As you navigate the maze you collect small white circles called Pac-Dots, collect Power Pellets, and interact with ghosts in a predator vs. prey situation but with roles switching depending on set criteria (AKA whether you've just collected a Power Pellet). The end goal being to collect all of the Pac-Dots

<div class="text-center pb-3">
      <img class="img-fluid" src="../img/Puckle/PacMan.jpg" width="800px">
</div>

I started off by creating our titular character as a yellow circle which could move in 4 directions: up, down, left and right. I defined a class to handle all collectables, their collisions with the player, and the point value they add to your total score. To distinguish between each type of collectible, I used Unity's tag system and would compare the tag when handling the player's collision with the collectible. Now that I had a player and some objects for it to interact with, I was still missing 2 core elements of the game, the walls of the maze and the ghosts which inhabited the maze.

The maze walls were pretty straight forward, I created a square that the player was incapable of moving through. These squares would be combined to shape the maze and any obstacles the player would encounter. While I say this was straight forward, it did take me a few tries to get this collision to work properly, and the way collisions were set up would lead to a bug with the Ghost's pathfinding that I wouldn't notice until the end of development.

<div class="text-center pb-3">
      <img class="img-fluid" src="../img/Puckle/Puckle_TheBeginning.PNG" width="800px">
</div>

## The Research / Rules

As the project's core elements came into being, I needed to get a better understanding of how Pac-Man works, specifically any rules related to how the ghosts behaved and the patterns for making the mazes. For this project, my research would involve use of the game wiki for both Pac-Man and Ms. Pac-Man, as well as sites which cataloged all of the mazes, and blogs which went into the different behaviors of the ghosts.

Ghosts in Pac-Man are well regarded for their behaviors, with each ghost having its own unique way of chasing the player. Beyond that each ghost also has flee behavior and a scatter behavior. When the player collects power pellets, the ghosts enter their flee behavior and try to get away from the player. The Scatter is when the ghosts navigate to their home concern of the maze for a duration. To keep things simple, I would only do the Flee and the basic Chase behavior.

## A* Pathfinding

Now that I’ve set the stage, let's dive into the reason most of you probably clicked on this post, A*. My implementation of A* is split into 2 classes, AStarSearch and PathNode. AStarSearch handles the actual searching while the PathNode class acts as a data type, containing the position of the Node, the map, the previous node and the 3 costs. The 3 types of cost are the path cost of a node (g), the estimated distance between a node and the goal (h), and combination of the previous 2 costs (f = g + h).

<div class="text-center pb-3">
      <img class="img-fluid" src="../img/Puckle/Puckle_HCost.PNG" width="800px">
</div>

AStarSearch takes in a representation of the maze, the start node (Ghost’s Position), and a goal node (Player’s Position). The first step of the algorithm is to check to see if the goal space contains a wall, if it does the algorithm checks the neighbors and will place the nearest open space as the new goal. Step 2 is to generate the costs for the start node (g being 0, h being the distance between the two path nodes, and f being the combination of the g and h costs) and declare the open and closed lists, with the open list containing the start node. These lists help to determine what nodes have been visited and what are yet to be visited.

Now we enter the main loop of the search, where with each iteration of the loop we get the Path Node with the lowest f cost, then check to see if it is the goal node and if not we keep going. First we remove the current node from the openList and add it to the closed list and check all of the current node’s neighbors. With each neighbor it checks if it’s already in the closed list, if not it calculates new cost values and checks to see if the new costs would be less than their current cost. If the new cost is less then the old cost, old costs are updated and the previous node value is set to the current node. Finally, if the Neighbor PathNode isn’t already in the open list, it gets added.

<div class="text-center pb-3">
      <img class="img-fluid" src="../img/Puckle/Puckle_Neighbor_Check.PNG" width="800px">
</div>

When the goal is reached, a list is generated by backtracking from the goal to the start using the previous node value stored in each node. Once the list is complete, it is reversed so the start node is index 0 and passed to the Ghost. The Ghosts use A* in 2 ways, to get a path to the player and to get a path for fleeing.

## The Problems

While this all seems pretty straightforward, its development wasn’t. At first, I was trying to figure out how I wanted to handle the implementation, I did a lot of research and found many different styles for implementing A* and in the process I found myself often trying to merge different styles or would pivot from one to the other when I got stumped. To get through this I had to restrict myself on what I could reference and boil it all down into what I needed, anything that was fluff got cut.

The next biggest issue I encountered was the impact of running A* for 4 ghosts, this had been something I was advised to not have run each frame due to how long the algorithm takes to run. I ended up setting a coroutine which would let around 5 seconds pass between updating the path, was this overkill… I won’t lie, 5 seconds was overkill. The issue that would come from the 5 second delay was that the AI can easily get tricked by timing movements so the AI thinks the player will be in one space, and stop there, meanwhile the player has since moved on and now a 5 second head start over the ghost, who has to wait for an update.

<div class="text-center pb-3">
      <img class="img-fluid" src="../img/Puckle/Puckle_AStar_Delay.PNG" width="800px">
</div>

The last major issue I encountered was that issue I teased back at the beginning with the walls. The player could sometimes get themselves partially inside the wall, while on screen it doesn’t look like anything is wrong, the AI gets confused because the player ends up registering as being in a weird in-between location which A* can't determine a valid path to. While I never implemented this fix, my intended solution was to replace movement and maze generation with a grid of specifically defined tiles, instead of it being general Unity coordinates that were approximated to tile-like dimensions.

<hr class="my-4">

Github: <a href="https://github.com/IanMelvin/GPR-340-Final" target="_blank">Project Repo</a>
