---
layout: post
title: Fun Over Function II
date: 2026-07-03
---

While finishing my little terminal game was as easy as I predicted in the last post, I remain just as pleasantly surprised.  
In the [last post](https://daud1.github.io/2026/06/27/fun-over-function.html), I was able to draw a maze using an array of user-determined dimensions and the depth first algorithm to create a solvable path through. To complete it, I needed to add a player character and listen to the player's keystrokes that mapped to directions in the maze.  
Since the maze co-ordinates correspond to the array indices and Curses' quirky (y,x) co-ordinate system, all this is fairly straightforward to do with existing curses methods, `getch` and `addstr`. In a while loop, the flow goes as follows:  

- listen for the arrow keystrokes from the player using `getch`
- check the maze to confirm the cell the player wants to move to is empty i.e value of the index in the maze is 0
- get the new co-ordinates for the cell by either adding or subtracting 1 to the appropriate co-ordinate componenent: {UP: (-1, 0), DOWN: (1, 0), LEFT: (0, -1), RIGHT: (0, 1)}
- clear (draw a space) the cell the player character is in and redraw it in the new cell using `addstr`

A few other considerations arise when factoring in the contraints that would make it functional. For example, to make it more visually appealing, I centered the maze horizontally. This required offsetting the x co-ordinate by half the space left after factoring in the width of the maze. This then had the knock-on effect of having to offset the row index by the same value so as to avoid out-of-bound errors when checking the maze if a cell is a path (0) or a wall (1). The complete code can be found in this [repo](https://github.com/daud1/cautious-octo-doodle.git)

| Start | Move | Win |
| -------------- | ----------- | ----------- |
| ![Start](/assets/images/maze_start.png) | ![Move](/assets/images/maze_move.png) | ![Win](/assets/images/maze_win.png) |

Each of these small tweaks I made offered surprisingly more fun/joy than establishing the basic functionality did. From catching the curses out-of-bound error when a player wins so I can display a win message, to ensuring the player's requested dimensions don't exceed the terminal window they're playing it in.  
Overall, this was a successful exercise in rekindling the joy that got me into this, especially given my prevailing unemployment. I find myself excited for whatever I'll make next.

In the wilderness of your pain, may your joy find you again. ;)
