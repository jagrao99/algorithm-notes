# Trees

## What is it?
A hierarchical data structure consisting of nodes connected by edges, with one root node and no cycles.

## Types:
1. **Binary Tree**: Each node has at most 2 children
2. **Binary Search Tree (BST)**: Left subtree < root < right subtree
3. **Balanced Trees**: AVL, Red-Black trees
4. **B-trees**: Used in databases
5. **Trie**: Prefix tree for strings

## Time Complexity (BST - Average Case):
- Search: O(log n)
- Insertion: O(log n)
- Deletion: O(log n)

## Time Complexity (BST - Worst Case):
- All operations: O(n) when tree becomes skewed

## When to Use:
- Hierarchical data representation
- Fast searching in sorted data
- Expression parsing
- File system representation

## Example Use Cases:
- File system directories
- Decision trees in AI
- Syntax trees in compilers
- Database indexing (B-trees)

## Tree Terminology:
- **Root**: Top node with no parent
- **Leaf**: Node with no children
- **Height**: Longest path from root to leaf
- **Depth**: Distance from root to a node
- **Subtree**: Tree rooted at any node
- **Parent/Child**: Direct connection relationship
- **Sibling**: Nodes with same parent

## Binary Tree Properties:
- **Maximum nodes at level i**: 2^i
- **Maximum nodes in tree of height h**: 2^(h+1) - 1
- **Minimum height for n nodes**: log₂(n)
- **Full Binary Tree**: Every node has 0 or 2 children
- **Complete Binary Tree**: All levels filled except possibly last
- **Perfect Binary Tree**: All internal nodes have 2 children, all leaves at same level

## Binary Search Tree (BST):
### Properties:
- Left subtree contains only nodes with keys less than root
- Right subtree contains only nodes with keys greater than root
- Both subtrees are also BSTs

### Traversal Methods:
1. **Inorder**: Left → Root → Right (gives sorted order)
2. **Preorder**: Root → Left → Right (good for copying tree)
3. **Postorder**: Left → Right → Root (good for deleting tree)
4. **Level Order**: Breadth-first traversal

### BST Operations:
- **Search**: Compare with root, go left or right
- **Insert**: Find correct position, add as leaf
- **Delete**: Three cases (leaf, one child, two children)

## Balanced Trees:

### AVL Trees:
- **Balance Factor**: Height difference between left and right subtrees ≤ 1
- **Rotations**: Single and double rotations to maintain balance
- **Guarantee**: O(log n) operations always

### Red-Black Trees:
- **Properties**: Nodes colored red or black with specific rules
- **Guarantee**: O(log n) operations, less rigid balancing than AVL
- **Used in**: Standard library implementations (C++ map, Java TreeMap)

## Tree Applications:

### File Systems:
- Directory structure representation
- Hierarchical organization
- Path traversal algorithms

### Compilers:
- **Abstract Syntax Trees (AST)**: Represent program structure
- **Parse Trees**: Show syntactic structure
- **Expression Trees**: Evaluate mathematical expressions

### Databases:
- **B-Trees**: Multi-way trees for disk storage
- **B+ Trees**: Leaf nodes linked for range queries
- **Index structures**: Fast data retrieval

### Game Development:
- **Decision Trees**: AI behavior
- **Scene Graphs**: 3D object hierarchies
- **Spatial Partitioning**: Octrees, Quadtrees

## Advanced Tree Concepts:

### Heap vs BST:
- **Heap**: Complete binary tree with heap property (parent ≥ children)
- **BST**: Search tree with ordering property
- **Different purposes**: Heap for priority queue, BST for searching

### Tree Balancing:
- **Why needed**: Prevent O(n) worst-case performance
- **Methods**: Rotations, restructuring
- **Self-balancing**: AVL, Red-Black, Splay trees

### Memory Considerations:
- **Pointer overhead**: Each node needs 2-3 pointers
- **Cache performance**: Tree traversal not cache-friendly
- **Memory layout**: Nodes scattered in memory

## Visual Examples

### Simple Binary Tree Structure
```
        [10]
       /    \
    [5]      [15]
    / \      /  \
 [3] [7]  [12] [20]
```
- Nodes labeled with values
- Root at 10, left/right children shown underneath

### Binary Search Tree (BST) Property
```
Initial insertion order: 10, 5, 15, 3, 7, 12, 20

        [10]
       /    \
    [5]      [15]
    / \      /  \
 [3] [7]  [12] [20]
```
- For each node, left child < parent < right child

### Traversal Visualization

#### Inorder Traversal (Left → Node → Right)
```
Stack: []
Visit sequence:
  Start at root (10)
  Go left to node 5, then left to 3
  Visit 3 → add to output: [3]
  Back to 5 → visit 5: [3,5]
  Go right to 7 → visit 7: [3,5,7]
  Back to 10 → visit 10: [3,5,7,10]
  Go right to 15, left to 12 → visit 12: [3,5,7,10,12]
  Back to 15 → visit 15: [3,5,7,10,12,15]
  Go right to 20 → visit 20: [3,5,7,10,12,15,20]
Final Inorder Sequence: 3, 5, 7, 10, 12, 15, 20
```

#### Preorder Traversal (Node → Left → Right)
```
Visit:
  10, 5, 3, 7, 15, 12, 20
```

#### Postorder Traversal (Left → Right → Node)
```
Visit:
  3, 7, 5, 12, 20, 15, 10
```

#### Level-Order (Breadth-First)
```
Queue: [10]
Visit order:
  Dequeue 10 → enqueue [5,15] → output [10]
  Dequeue 5 → enqueue [3,7]  → output [10,5]
  Dequeue 15 → enqueue [12,20] → output [10,5,15]
  Continue until queue empty
Final Level-Order: 10, 5, 15, 3, 7, 12, 20
```

### AVL Tree Rotation Example
```
Insert in order: 10, 5, 4

Before rotation:
     [10]
     /
   [5]
   /
 [4]

Balance factor at 10 = 2 → left-left case
Single Right Rotation at 10:
        [5]
       /   \
     [4]   [10]
```

### Deletion in BST (Three Cases)
```
Deleting leaf node (7):
        [10]
       /    \
    [5]      [15]
     |       /  \
    [3]    [12] [20]

Deleting node with one child (5):
        [10]
       /    \
    [3]      [15]
           /    \
        [12]    [20]

Deleting node with two children (10):
Find inorder successor (12): replace 10 with 12, then delete 12 leaf
        [12]
       /    \
    [3]      [15]
             \
            [20]
```
