MAZE SOLVER - BFS, GREEDY BEST-FIRST SEARCH, AND A* SEARCH
=============================================================

DESCRIPTION
-----------
This program solves a maze using three different search algorithms:
1. Breadth-First Search (BFS)       - uninformed search
2. Greedy Best-First Search (GBFS)  - informed search using f(n) = h(n)
3. A* Search                        - informed search using f(n) = g(n) + h(n)

The heuristic used for GBFS and A* is the Manhattan distance,
h(n) = |row - goal_row| + |col - goal_col|, which is admissible since
movement is restricted to up/down/left/right with unit cost per move.

For each algorithm, the program prints:
- Whether a solution was found
- Number of states explored
- Maximum frontier size reached
- Path cost (number of moves)
- Runtime (in seconds)
- The maze with the solution path marked using '*'

It also saves a solution image for each algorithm.


REQUIREMENTS
------------
- Python 3.x
- Pillow (PIL) library, required only for generating output images

Install Pillow if not already installed:
    pip install Pillow

No other external libraries are required. The program uses only the
standard library modules: sys, heapq, time.


FILES INCLUDED
---------------
Maze.py        - main program (BFS, GBFS, A* implementations)
maze1.txt      - simple maze (single path, no branching)
maze2.txt      - maze with multiple possible paths / dead-end branches
maze3.txt      - maze with dead ends / misleading routes
README.txt     - this file


HOW TO RUN
----------
Run the program from the terminal/PowerShell, passing the maze file
as a command-line argument:

    python Maze.py maze1.txt
    python Maze.py maze2.txt
    python Maze.py maze3.txt

Each run automatically executes all three algorithms (BFS, GBFS, A*)
in sequence on the given maze file and prints their results to the
terminal.


OUTPUT IMAGES
--------------
After each run, three image files are generated in the same folder:
    maze_BFS.png
    maze_GBFS.png
    maze_Astar.png

IMPORTANT: These filenames are the same for every maze run, so the
images will be OVERWRITTEN each time a new maze is solved. Rename or
move the images before running the next maze file, for example:

    ren maze_BFS.png maze1_BFS.png
    ren maze_GBFS.png maze1_GBFS.png
    ren maze_Astar.png maze1_Astar.png

(On macOS/Linux, use "mv" instead of "ren".)

Image color key:
    Red    = Start (A)
    Green  = Goal (B)
    Dark   = Wall
    Yellow/Light green = Solution path
    Light red (if enabled) = Explored states


MAZE FILE FORMAT
-----------------
- Exactly one 'A' (start) and one 'B' (goal) must be present.
- '#' represents a wall.
- ' ' (space) represents an open, walkable cell.
- Movement is restricted to up, down, left, right (no diagonals).


NOTES
-----
- If a maze has no solution, the program raises an exception
  ("no solution") instead of crashing silently.
- GBFS is not guaranteed to find the shortest path, since it only
  considers h(n) and ignores path cost already traveled.
- A* is guaranteed to find the shortest path here, since the Manhattan
  distance heuristic is admissible for this grid (no diagonal moves,
  unit move cost).
