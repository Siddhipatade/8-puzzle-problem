  # 8-puzzle problem using A* algorithm

 _N-Puzzle or Sliding Puzzle is a popular puzzle that consists of **N** tiles where **N** can be 8, 15, 24 and so on._

    In our example N = 8. 
    The puzzle is divided into sqrt(N+1) rows and sqrt(N+1) columns.
    8-Puzzle will have 3 rows and 3 columns. 
    
The puzzle consists of _8 tiles_ and one empty space where the tiles can be moved. 
_Start_ and _Goal  state_ of the puzzle are provided. 
The puzzle can be solved by moving the tiles one by one in the single empty space and thus achieving the Goal state.

The tiles in the initial(start) state can be moved in the empty space in a particular order and thus achieve the goal state.

### `Rules for solving the puzzle`

Instead of moving the tiles in the empty space we can visualize moving the empty space in place of the tile, basically swapping the tile with the empty space. The empty space can only move in four directions viz.,
1. **Up**
2. **Down**
3. **Right** or
4. **Left**

The _**empty space cannot move diagonally**_ and can take _**only one step at a time**_ (i.e. move the empty space one position at a time).

# A* Algorithm
**A*** is a computer algorithm that is widely used in pathfinding and graph traversal, the process of plotting an efficiently traversable path between multiple points, called nodes.

_The key feature of the **A*** algorithm is that it keeps a track of each visited node_ which helps in ignoring the nodes that are already visited, saving a huge amount of time. 
It also has a list that holds all the nodes that are left to be explored and it chooses the most optimal node from this list, thus saving time not exploring unnecessary or less optimal nodes.

So I use two lists namely **'Open list'** and **'Closed list'** the **'Open list'** contains all the nodes that are being generated and are not existing in the **'Closed list'** and each node explored after it's neighboring nodes are discovered is put in the **'Closed list'** and the neighbors are put in the **'Open list'** this is how the nodes expand. 
Each node has a pointer to its parent so that at any given point it can retrace the path to the parent. Initially, the open list holds the start(Initial) node. The next node chosen from the open list is based on its **'f-score'**, the node with the least **'f-score'** is picked up and explored.

      f-score = h-score + g-score

**A*** uses a combination of heuristic value (h-score: how far the goal node is) as well as the **'g-score'** (i.e. the number of nodes traversed from the start node to current node).
In 8-Puzzle problem, define the **'h-score'** as the number of misplaced tiles by comparing the current state and the goal state or summation of the Manhattan distance between misplaced nodes.
**'g-score'** will remain as the number of nodes traversed from start node to get to the current node.

Calculate the **'h-score'** by comparing the initial(current) state and goal state and counting the number of misplaced tiles.

Thus, **h-score** = 5 and **g-score** = 0 as the number of nodes traversed from the start node to the current node is 0.


# How A* solves the 8-Puzzle problem.

We first move the empty space in all the possible directions in the start state and calculate the **'f-score'** for each state. 
This is called expanding the current state.
After expanding the current state, it is pushed into the **'Closed list'** and the newly generated states are pushed into the **'Open list'**. 
A state with the least **'f-score'** is selected and expanded again. This process continues until the goal state occurs as the current state. 

Basically, here we are providing the algorithm a measure to choose its actions. The algorithm chooses the best possible action and proceeds in that path.
This solves the issue of generating redundant child states, as the algorithm will expand the node with the least **'f-score'**.
