---
layout: essay
type: essay
title: "Developing a Pac-Man clone using A*"
# All dates must be YYYY-MM-DD format!
date: 2023-03-29
published: false
labels:
  - Game Programming
  - A*
  - AI
---

In the fall semester of 2022, I recreated the classic arcade game, Pac-Man, in Unity 2D. This project had 2 main caviots, I needed to create the AI using A* pathfinding and the maze needed to have parts of it generated randomly every time the game was run. This post will go over the process of development, the ups and downs I encountered, and all of the lessions I learned along the way.

[Insert media here]

## The Basics

Before I can get into any of the fancy talk with A* and the maze generation, I want to talk about what these system were built on / to work with: the core gameplay elements. As many of you might be familiar with, Pac-Man is a game where you as the player, navigate a maze from a top down perspective, collect small white circles called Pac-Dots, collect Power Pellets, and interact with ghosts in a preditor vs. prey situation but with roles switching depending on set criteria (AKA whether you've just collected a Power Pellet).

[Insert image of a game of pac-man]

I started off by creating our titular character as a yellow circle which could move in 4 directions: up, down, left and right. From I defined a class to handle all collectables, their collisions with the player, and the point value. To distinguish between each type of collectable, I used Unity's tag system  and would compare the tag when handling the player collision. Now that I had a player and some objects for it to interact with, I still missing 2 cor elements of the game, the walls of the maze and the ghosts which inhabited the maze.

The maze walls were pretty straight forward, I created a square that the player was incapable of moving through. The individual squares of wall would allow for shape making and placement when generating the maze. While I say this was straight forward, it did take me a few tries to get this collsion to work properly, and the way collisions were set up would lead to a bug with the Ghost AI I wouldn't notice till the end of development. 

[Insert media]

## The Research / Rules

As the project's core elements came into being, I needed to get a better understanding of how Pac-Man work, specifically any rules releated to the mazes and how the ghosts behaved. For this project my research would involve use of both the game wiki's for both Pac-Man and Ms. Pac-Man, sites which catalogued all of the mazes, and blogs which went into the different behavior of each of the ghosts.

For the mazes, I anaylsed the original Pac-Man maze and all 4 Ms. Pac-Man mazes attempting to generate a set of rules I could use in my own maze generation. The first rule I defined was that each half of the maze was a mirror image of itself, meaning I only had to generate half a maze and then fold the generated half onto the other half. The second rule was for consistent elements of the maze, such as warp tunnels and the ghost spawn zone. The ghost spawn zone was a box located in the middle of the map, skewing towards the upper half, and maintained a consistant position. The warp tunnels varried depending on the map, but had a max and minimun height they could be place on.
