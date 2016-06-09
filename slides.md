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

## Challenge 1

John and Mike live in a _strange city_, which resembles New York.
The city can be represented as a matrix of N rows and M columns (NxM),
and each block can be represented as either a 0 (can pass through),
or a -1 (cannot pass through).

John can travel on 4 directions: _up_, _down_, _left_ and _right_.

Given John's and Mike's position in the matrix, **find out the shortest
path from John to Mike**.

---
## Input

N, M - integers

X[N][M] - matrix of Integers (matrix row,column numbering starts at 0)


X1, Y1 - the position of John (row, column)

X2, Y2 - the position of Mike (row, column)

---
## Input (2)

The numbering of the rows start at 0 and finishes at N-1

The numbering of columns starts at 0 and finishes at M-1

If there is no path from John to Mike, return -1

---
Javascript
#### `pathfinder(n, m, matrix, x1, y1, x2, y2)`

- `n` (`Integer`) number of rows
- `m` (`Integer`) number of columns
- `matrix` (`Array of Array of Integers`) the matrix describind the city
- `x1` the row of John
- `y1` the column of John
- `x2` the row of Mike
- `y2` the column of Mike
- returns: (`Integer`) the number of moves required John has to make to reach
Mike's position

---
Ruby
#### `Pathfinder.new(n, m, matrix, x1, x2, y2).solve`

- `n` (`Integer`) number of rows
- `m` (`Integer`) number of columns
- `matrix` (`Array of Array of Integers`) the matrix describind the city
- `x1` the row of John
- `y1` the column of John
- `x2` the row of Mike
- `y2` the column of Mike
- returns: (`Integer`) the number of moves required John has to make to reach
Mike's position

---

### Example

N: 4
M: 5

John's position is: (0,0)

Mike's position is: (3,4)

Matrix looks like this:
| 0 | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| 0 | -1 | -1 | 0  | -1 |
| 0 | 0  | 0  | -1 | 0  |
| 0 | -1 | 0  | 0  | 0  |

---

| J | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| 0 | -1 | -1 | 0  | -1 |
| 0 | 0  | 0  | -1 | 0  |
| 0 | -1 | 0  | 0  | M  |

---

| J | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| **1** | -1 | -1 | 0  | -1 |
| 0 | 0  | 0  | -1 | 0  |
| 0 | -1 | 0  | 0  | M  |

---

| J | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| 1 | -1 | -1 | 0  | -1 |
| **2** | 0  | 0  | -1 | 0  |
| 0 | -1 | 0  | 0  | M  |

---

| J | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| 1 | -1 | -1 | 0  | -1 |
| 2 | **3**  | 0  | -1 | 0  |
| 0 | -1 | 0  | 0  | M  |

---

| J | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| 1 | -1 | -1 | 0  | -1 |
| 2 | 3| **4**  | -1 | 0  |
| 0 | -1 | 0  | 0  | M  |

---

| J | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| 1 | -1 | -1 | 0  | -1 |
| 2 | 3| 4| -1 | 0  |
| 0 | -1 | **5**  | 0  | M  |

---

| J | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| 1 | -1 | -1 | 0  | -1 |
| 2 | 3| 4| -1 | 0  |
| 0 | -1 | 5| **6**  | M  |

---

| J | 0  | 0  | 0  | 0  |
|---|----|----|----|----|
| 1 | -1 | -1 | 0  | -1 |
| 2 | 3  | 4  | -1 |  0 |
| 0 | -1 | 5| 6  | **7** ~ M  |

---

Answer: 7

(0,0)->(1,0)->(2,0)->(2,1)->(2,2)->(3,2)->(3,3)->(3,4)

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
## Challenge 2

John is living in London. He now has to travel across the city to visit his
good friend Charlie. However, John is not very well acquainted with the
transportation system in London and still finds it very confusing (and expensive).

John knows a list of stops from the city and how expensive is to travel from one
to the other. He also knows where he wants to meet his friend Charlie.

Can you help John select the cheapest way to see his friend Charlie?

---

## Input
N - the number of pairs of stations and the cost to go from one to the other
Links - `Array` of `tuples` formed of (start_station, end_station, cost), where every
element of the tuple is an `Integer`

---
Javascript
#### `findTheWay(links, start_station, end_station)`

- `links` (`Array` of `tuples`) - describing the cost between two stations (as
per previous slide)
- `start` (`Integer`) the start station, from which John starts
- `end_station` (`Integer`) the end station where he meets Charlie
- returns: (`Integer`, `Integer`) - first the number of stations through which
John passes, followed by the total cost of the trip

---
Ruby

#### `FindTheWay.new(links, start_station, end_station)`

- `links` (`Array` of `tuples`) - describing the cost between two stations (as
per previous slide)
- `start` (`Integer`) the start station, from which John starts
- `end_station` (`Integer`) the end station where he meets Charlie
- returns: (`Integer`, `Integer`) - first the number of stations through which
John passes, followed by the total cost of the trip

---

## Djisktra's Algorithm

- Have an array for visited stations (visited)
- Have an array for the cost of getting to each station (costs); initialize this
with INFINITY (... or close to it)
- Have an array of current nodes, sorted by the lowest cost of the node

---

## Djikstra's Algorithm

1. Add the start node to the `current_nodes` array, with a cost of 0

2. Pick the node with the least cost from `current_nodes` (selected)

3. Add all of the nodes you can reach from the selected node to the
`current_nodes` array, and update their cost in the `costs` array, by summing up
the cost of the `selected` node and the cost of the link from the selected node
to the node

4. Mark the `selected` node as visited, and return to step 2
