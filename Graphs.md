# Graphs

## What is it?
A collection of vertices (nodes) connected by edges, representing relationships between entities.

## Types:
1. **Directed vs Undirected**: Edges have direction or not
2. **Weighted vs Unweighted**: Edges have weights/costs or not
3. **Connected vs Disconnected**: All vertices reachable or not
4. **Cyclic vs Acyclic**: Contains cycles or not

## Representations:
1. **Adjacency Matrix**: 2D array
2. **Adjacency List**: Array of lists
3. **Edge List**: List of edges

## Common Algorithms:
- **Traversal**: DFS, BFS
- **Shortest Path**: Dijkstra's, Bellman-Ford
- **Minimum Spanning Tree**: Kruskal's, Prim's

## When to Use:
- Modeling networks (social, computer, transportation)
- Finding shortest paths
- Dependency resolution
- Web crawling

## Example Use Cases:
- Social networks (friendship connections)
- GPS navigation systems
- Network routing protocols
- Dependency graphs in build systems

## Graph Terminology:
- **Vertex/Node**: Individual point in graph
- **Edge**: Connection between two vertices
- **Degree**: Number of edges connected to a vertex
- **Path**: Sequence of vertices connected by edges
- **Cycle**: Path that starts and ends at same vertex
- **Connected Component**: Maximal set of connected vertices

## Graph Representations Comparison:

### Adjacency Matrix:
```
   A B C D
A [0 1 1 0]
B [1 0 0 1]  
C [1 0 0 1]
D [0 1 1 0]
```
- **Space**: O(V²)
- **Edge lookup**: O(1)
- **Add vertex**: O(V²) - need to resize matrix
- **Good for**: Dense graphs, quick edge lookups

### Adjacency List:
```
A → [B, C]
B → [A, D]
C → [A, D]  
D → [B, C]
```
- **Space**: O(V + E)
- **Edge lookup**: O(degree)
- **Add vertex**: O(1)
- **Good for**: Sparse graphs, memory efficiency

### Edge List:
```
[(A,B), (A,C), (B,D), (C,D)]
```
- **Space**: O(E)
- **Edge lookup**: O(E)
- **Good for**: Simple algorithms, minimal storage

## Graph Traversal Algorithms:

### Depth-First Search (DFS):
- **Strategy**: Go as deep as possible before backtracking
- **Implementation**: Stack (recursive or explicit)
- **Time**: O(V + E)
- **Space**: O(V) for recursion stack
- **Uses**: Topological sorting, detecting cycles, path finding

### Breadth-First Search (BFS):
- **Strategy**: Explore all neighbors before going deeper
- **Implementation**: Queue
- **Time**: O(V + E)
- **Space**: O(V) for queue
- **Uses**: Shortest path (unweighted), level-order traversal

## Shortest Path Algorithms:

### Dijkstra's Algorithm:
- **Purpose**: Single-source shortest path (non-negative weights)
- **Strategy**: Greedy, always pick closest unvisited vertex
- **Time**: O((V + E) log V) with priority queue
- **Uses**: GPS navigation, network routing

### Bellman-Ford Algorithm:
- **Purpose**: Single-source shortest path (handles negative weights)
- **Strategy**: Relax all edges V-1 times
- **Time**: O(VE)
- **Uses**: Detecting negative cycles, currency arbitrage

### Floyd-Warshall Algorithm:
- **Purpose**: All-pairs shortest path
- **Strategy**: Dynamic programming
- **Time**: O(V³)
- **Uses**: Dense graphs, transitive closure

## Minimum Spanning Tree:

### Kruskal's Algorithm:
- **Strategy**: Sort edges, add smallest edge that doesn't create cycle
- **Data Structure**: Disjoint Set Union (Union-Find)
- **Time**: O(E log E)
- **Good for**: Sparse graphs

### Prim's Algorithm:
- **Strategy**: Start from vertex, always add minimum edge to tree
- **Data Structure**: Priority queue
- **Time**: O((V + E) log V)
- **Good for**: Dense graphs

## Special Graph Types:

### Directed Acyclic Graph (DAG):
- **Properties**: Directed, no cycles
- **Applications**: Task scheduling, dependency resolution
- **Algorithms**: Topological sorting, longest path

### Bipartite Graph:
- **Properties**: Vertices can be colored with 2 colors
- **Test**: Graph is bipartite iff no odd-length cycles
- **Applications**: Matching problems, two-coloring

### Planar Graph:
- **Properties**: Can be drawn without edge crossings
- **Euler's Formula**: V - E + F = 2
- **Applications**: Circuit design, map coloring

## Graph Applications:

### Social Networks:
- **Vertices**: People
- **Edges**: Friendships, follows, interactions
- **Algorithms**: Friend recommendations, influence propagation

### Transportation Networks:
- **Vertices**: Locations (cities, intersections)
- **Edges**: Roads, flights, routes
- **Algorithms**: Shortest path, traffic optimization

### Computer Networks:
- **Vertices**: Routers, computers
- **Edges**: Network connections
- **Algorithms**: Routing protocols, network reliability

### Web Graph:
- **Vertices**: Web pages
- **Edges**: Hyperlinks
- **Algorithms**: PageRank, web crawling

## Implementation Considerations:

### Memory Usage:
- **Adjacency Matrix**: O(V²) - suitable for dense graphs
- **Adjacency List**: O(V + E) - suitable for sparse graphs
- **Choose based on**: Graph density, operations needed

### Performance Trade-offs:
- **Matrix**: Fast edge lookups, high memory usage
- **List**: Memory efficient, slower edge lookups
- **Hybrid approaches**: For specific use cases

### Dynamic Graphs:
- **Adding vertices/edges**: Consider representation efficiency
- **Removing vertices/edges**: May require cleanup
- **Graph streaming**: Handle large graphs that don't fit in memory

## Visual Examples

### Basic Graph Structures

#### Undirected Graph:
```
Simple Undirected Graph:
    A ——— B
    |     |
    |     |
    C ——— D

Adjacency representation:
A connects to: B, C
B connects to: A, D  
C connects to: A, D
D connects to: B, C
```

#### Directed Graph (Digraph):
```
Simple Directed Graph:
    A ——→ B
    ↑     ↓
    |     |
    C ←—— D

Adjacency representation:
A → B
B → D
C → A  
D → C
```

#### Weighted Graph:
```
Weighted Undirected Graph:
      5      3
    A ——— B ——— C
    |     |     |
   2|    4|     |7
    |     |     |
    D ——— E ——— F
        6     1

Edge weights shown on connections
Used for: Shortest path, minimum spanning tree
```

### Graph Representations Visualized

#### 1. Adjacency Matrix:
```
Graph:     A ——— B
           |     |
           C ——— D

Adjacency Matrix:
     A  B  C  D
  A [0, 1, 1, 0]
  B [1, 0, 0, 1]
  C [1, 0, 0, 1]
  D [0, 1, 1, 0]

Matrix[i][j] = 1 if edge exists, 0 otherwise
Matrix[i][j] = weight for weighted graphs
```

#### 2. Adjacency List:
```
Same Graph as Above:

Adjacency List:
A: [B, C]
B: [A, D]
C: [A, D]
D: [B, C]

Each vertex stores list of its neighbors
More memory efficient for sparse graphs
```

#### 3. Edge List:
```
Same Graph as Edge List:

Edge List:
[(A,B), (A,C), (B,D), (C,D)]

Simple list of all edges
Good for algorithms that process all edges
```

### Graph Traversal Algorithms

#### Depth-First Search (DFS):
```
Graph:         1
              / \
             2   3
            /   / \
           4   5   6

DFS Traversal (starting from 1):
Step 1: Visit 1, push neighbors → Stack: [2, 3]
   🟢1
  / \
 2   3

Step 2: Pop 3, visit 3, push neighbors → Stack: [2, 5, 6]
   🟢1
  / \
 2  🟢3
   / \
  5   6

Step 3: Pop 6, visit 6 → Stack: [2, 5]
   🟢1
  / \
 2  🟢3
   / \
  5  🟢6

Step 4: Pop 5, visit 5 → Stack: [2]
   🟢1
  / \
 2  🟢3
   /  \
 🟢5  🟢6

Step 5: Pop 2, visit 2, push neighbors → Stack: [4]
  🟢1
  / \
🟢2 🟢3
 /   / \
4  🟢5 🟢6

Step 6: Pop 4, visit 4 → Stack: []
   🟢1
  / \
🟢2  🟢3
/    / \
🟢4 🟢5 🟢6

DFS Order: 1 → 3 → 6 → 5 → 2 → 4
```

#### Breadth-First Search (BFS):
```
Same Graph as Above:

BFS Traversal (starting from 1):
Step 1: Visit 1, enqueue neighbors → Queue: [2, 3]
   🟢1
  / \
 2   3

Step 2: Dequeue 2, visit 2, enqueue neighbors → Queue: [3, 4]
  🟢1
  / \
🟢2  3
 /
4

Step 3: Dequeue 3, visit 3, enqueue neighbors → Queue: [4, 5, 6]
  🟢1
  / \
🟢2 🟢3
 /   / \
4   5   6

Step 4: Dequeue 4, visit 4 → Queue: [5, 6]
   🟢1
  / \
🟢2  🟢3
/    / \
🟢4  5   6

Step 5: Dequeue 5, visit 5 → Queue: [6]
   🟢1
  / \
🟢2  🟢3
/    / \
🟢4 🟢5  6

Step 6: Dequeue 6, visit 6 → Queue: []
   🟢1
  / \
🟢2  🟢3
/    / \
🟢4 🟢5 🟢6

BFS Order: 1 → 2 → 3 → 4 → 5 → 6
Level-by-level traversal
```

### Shortest Path Algorithms

#### Dijkstra's Algorithm:
```
Weighted Graph:
      2      4
    A ——— B ——— D
    |     |     |
   1|    3|     |2
    |     |     |
    C ——— E ——— F
        1     3

Finding shortest path from A to F:

Step 1: Initialize distances
A: 0, B: ∞, C: ∞, D: ∞, E: ∞, F: ∞
Unvisited: {A, B, C, D, E, F}
Current: A (distance 0)

Step 2: Update neighbors of A
A: 0, B: 2, C: 1, D: ∞, E: ∞, F: ∞
Unvisited: {B, C, D, E, F}
Current: C (distance 1)

Step 3: Update neighbors of C
A: 0, B: 2, C: 1, D: ∞, E: 2, F: ∞
Unvisited: {B, D, E, F}
Current: B (distance 2)

Step 4: Update neighbors of B
A: 0, B: 2, C: 1, D: 6, E: 2, F: ∞
Unvisited: {D, E, F}
Current: E (distance 2)

Step 5: Update neighbors of E
A: 0, B: 2, C: 1, D: 6, E: 2, F: 5
Unvisited: {D, F}
Current: F (distance 5)

Shortest path A → F: A → C → E → F (total distance: 5)
Path visualization:
A ——→ C ——→ E ——→ F
  1     1      3
```

### Minimum Spanning Tree

#### Kruskal's Algorithm:
```
Weighted Graph:
      5      3
    A ——— B ——— C
    |     |     |
   2|    4|     |7
    |     |     |
    D ——— E ——— F
        6     1

Step 1: Sort edges by weight
Edges: [(E,F,1), (A,D,2), (B,C,3), (B,E,4), (A,B,5), (D,E,6), (C,F,7)]

Step 2: Add edges without creating cycles

Add (E,F,1):
    A     B ——— C
    |     |     |
    |     |     |
    D     E ——— F

Add (A,D,2):
    A     B ——— C
    |     |     |
    |     |     |
    D     E ——— F

Add (B,C,3):
    A     B ——— C
    |     |     |
    |     |     |
    D     E ——— F

Add (B,E,4):
    A     B ——— C
    |     |     |
    |     |     |
    D     E ——— F

Add (A,B,5):
    A ——— B ——— C
    |     |     |
    |     |     |
    D     E ——— F

Skip (D,E,6) - would create cycle
Skip (C,F,7) - would create cycle

Minimum Spanning Tree:
Total weight: 1 + 2 + 3 + 4 + 5 = 15
```

### Special Graph Types

#### Bipartite Graph:
```
A bipartite graph with two sets:

Set 1: {A, B, C}    Set 2: {X, Y, Z}

    A ————————— X
    |           |
    |           |
    B ————————— Y
    |           |
    |           |
    C ————————— Z

Properties:
- Vertices can be colored with 2 colors
- No edges within the same set
- Used for matching problems
```

#### Directed Acyclic Graph (DAG):
```
Task Dependencies (Topological Order):

    A ——→ B ——→ D
    |           |
    ↓           ↓
    C ——————→ E ——→ F

Topological Sort: A → B → C → D → E → F
or: A → C → B → D → E → F

Valid execution orders for dependent tasks
Used in: Build systems, course prerequisites
```

#### Cycle Detection:
```
Graph with Cycle:
    A ——→ B
    ↑     ↓
    |     |
    D ←—— C

DFS Cycle Detection:
1. Start at A, mark as visiting
2. Go to B, mark as visiting  
3. Go to C, mark as visiting
4. Go to D, mark as visiting
5. Try to go to A - already visiting → CYCLE FOUND!

Cycle: A → B → C → D → A
```

### Graph Applications Visualized

#### Social Network:
```
Facebook Friend Network:

    Alice ————— Bob
      |          |
      |          |
    Carol ——— David ——— Eve
      |          |
      |          |
    Frank ——— Grace

Features:
- Vertices: People
- Edges: Friendships
- Algorithms: Friend recommendations, shortest connection path
```

#### Road Network:
```
City Road Network:

    Mall ←—5km—→ Home
     |            |
   3km|            |2km
     |            |
    Work ←—4km—→ School
     |            |
   1km|            |6km
     |            |
   Park ←—3km—→ Library

Features:
- Vertices: Locations
- Edges: Roads with distances
- Algorithms: Shortest route (GPS navigation)
```

#### Web Page Links:
```
Website Link Structure:

    Home ——→ About
     |        |
     ↓        ↓
   Blog ——→ Contact
     |        ↑
     ↓        |
   Archive ——→

Features:
- Vertices: Web pages
- Edges: Hyperlinks
- Algorithms: PageRank, web crawling
```

### Graph Complexity Visualization

#### Sparse vs Dense Graphs:
```
Sparse Graph (few edges):
    A     B     C
    |           |
    D     E ——— F

Edges: 3, Vertices: 6
Edge density: 3/(6×5/2) = 3/15 = 20%

Dense Graph (many edges):
    A ——— B ——— C
    |\ /| |\ /|
    | X | | X |
    |/ \| |/ \|
    D ——— E ——— F

Edges: 12, Vertices: 6  
Edge density: 12/15 = 80%

Storage implications:
- Sparse: Adjacency list preferred
- Dense: Adjacency matrix acceptable
```

### Memory Layout Comparison

#### Adjacency Matrix Layout:
```
4x4 Matrix in Memory:
[0,1,0,1,1,0,1,0,0,1,0,1,1,0,1,0]
 ↑       ↑       ↑       ↑
Row 0   Row 1   Row 2   Row 3

Pros: O(1) edge lookup, cache-friendly for dense graphs
Cons: O(V²) space, wasteful for sparse graphs
```

#### Adjacency List Layout:
```
Array of Lists in Memory:
Index 0: [1,3] → Node → Node → NULL
Index 1: [0,2] → Node → Node → NULL  
Index 2: [1,3] → Node → Node → NULL
Index 3: [0,2] → Node → Node → NULL

Pros: O(V+E) space, efficient for sparse graphs
Cons: O(degree) edge lookup, pointer overhead
```
