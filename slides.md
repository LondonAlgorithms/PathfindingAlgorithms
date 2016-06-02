# Pathfinding Algorithms

Alex

@alexstoick

---

# What does pathfinding mean?

---

![pathfinding](http://previews.123rf.com/images/michaeljung/michaeljung1407/michaeljung140700063/29701637-confused-tourist-on-the-street-looking-at-a-map-Stock-Photo.jpg)

---

# Actually...

![pathfinding_real](http://www.olhovsky.com/wp/wp-content/uploads/2011/03/hex_path_finding_work.png)

---

## Types of pathfinding algorithms

- Breadth First Search (BFS)
- Depth First Search (DFS)

---
### Breadth first search
![bfs](https://upload.wikimedia.org/wikipedia/commons/5/5d/Breadth-First-Search-Algorithm.gif)

---

### Depth first search
![dfs](https://upload.wikimedia.org/wikipedia/commons/7/7f/Depth-First-Search.gif)

---

Lee's Algorithm

- Implements a simple BFS algorithm
- Has a start position
- Has a goal(end) position
- Implementation that is based on a matrix

---
Lee's Algorithm - Step 1

- Add start position to array of positions to be inspected

---

Lee's Algorithm - Step 2

- Pick first element from array
- Add all visitable neighbours of this element to the end of the array
- Pop element from the array

---

Lee's Algorithm - Step 3

- Repeat *Step 2* until you reach the goal position

---

## Challenge 1: Romeo & Juliet

Romeo and Juliet live in a _strange city_.
The city can be represented as a matrix of N rows and M columns (NxM),
and each block can be represented as either a 0 (can pass through),
or a 1 (cannot pass through).

Given Romeo's and Juliet's position in the matrix, **find out the shortest
path from Romeo to Juliet**.

---

#### `romeoAndJuliet(n, m, matrix, romeo, juliet)`
- param1: `n` (`Integer`) number of rows
- param1: `m` (`Integer`) number of columns
- param2: `matrix` (`Array of Array of Integers`) the matrix describind Romeo
and Juliet's city
- returns: (`Integer`) the number of moves required to reach Juliet from
Romeo's place

---
