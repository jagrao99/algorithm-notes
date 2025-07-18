# Heaps

## What is it?
A specialized tree-based data structure that satisfies the heap property: parent nodes are either greater than (max-heap) or less than (min-heap) their children.

## Types:
1. **Max-Heap**: Parent ≥ children
2. **Min-Heap**: Parent ≤ children
3. **Binary Heap**: Complete binary tree
4. **Fibonacci Heap**: More complex, better for some operations

## Time Complexity (Binary Heap):
- Find Min/Max: O(1)
- Insert: O(log n)
- Delete Min/Max: O(log n)
- Build Heap: O(n)

## When to Use:
- Priority queues
- Heap sort algorithm
- Finding k largest/smallest elements
- Graph algorithms (Dijkstra's, Prim's)

## Example Use Cases:
- Operating system task scheduling
- Dijkstra's shortest path algorithm
- Huffman coding
- Finding median in data streams

## Heap Properties:

### Binary Heap Structure:
- **Complete Binary Tree**: All levels filled except possibly last
- **Array Representation**: Efficient storage without pointers
- **Parent-Child Relationship**:
  - Parent of node i: (i-1)/2
  - Left child of node i: 2*i + 1
  - Right child of node i: 2*i + 2

### Heap Property:
- **Max-Heap**: Every parent ≥ its children
- **Min-Heap**: Every parent ≤ its children
- **Not a BST**: No ordering between siblings
- **Weak ordering**: Only parent-child relationship matters

## Heap Operations:

### Insert (Bubble Up):
1. Add element at end of array
2. Compare with parent
3. Swap if heap property violated
4. Repeat until heap property restored
- **Time**: O(log n)

### Extract Min/Max (Bubble Down):
1. Replace root with last element
2. Remove last element
3. Compare with children
4. Swap with smaller/larger child
5. Repeat until heap property restored
- **Time**: O(log n)

### Build Heap (Heapify):
- **Bottom-up approach**: Start from last non-leaf, heapify down
- **Time**: O(n) - better than n insertions
- **Key insight**: Most nodes are leaves, need minimal work

## Heap Variants:

### Binary Heap:
- **Most common**: Simple implementation
- **Array-based**: No pointers needed
- **Operations**: Standard insert, extract, heapify

### d-ary Heap:
- **Each node**: Up to d children
- **Trade-off**: Shorter height vs. more comparisons per level
- **Use case**: When comparisons are cheap relative to movement

### Fibonacci Heap:
- **Advanced structure**: Better amortized performance
- **Operations**: 
  - Insert: O(1) amortized
  - Extract-min: O(log n) amortized
  - Decrease-key: O(1) amortized
- **Use case**: Graph algorithms with many decrease-key operations

## Priority Queue Implementation:

### Interface:
```
insert(element, priority)
extractMax()/extractMin()
peek()
changePriority(element, newPriority)
```

### Applications:
- **Task Scheduling**: CPU processes with priorities
- **Event Simulation**: Process events in time order
- **Graph Algorithms**: Dijkstra's, Prim's MST
- **Huffman Coding**: Build optimal prefix codes

## Heap Sort Algorithm:

### Process:
1. **Build heap** from input array: O(n)
2. **Repeatedly extract max**: O(n log n)
3. **Place at end** of array

### Characteristics:
- **Time**: O(n log n) worst case
- **Space**: O(1) - in-place sorting
- **Not stable**: Equal elements may change relative order
- **Not adaptive**: Performance doesn't improve on partially sorted data

## Advanced Heap Applications:

### k-way Merge:
- **Problem**: Merge k sorted arrays
- **Solution**: Min-heap with one element from each array
- **Time**: O(n log k) where n is total elements

### Top-k Elements:
- **Problem**: Find k largest/smallest elements
- **Solution**: Min-heap of size k for largest, Max-heap for smallest
- **Time**: O(n log k)

### Median Finding:
- **Problem**: Maintain median of streaming data
- **Solution**: Two heaps (max-heap for smaller half, min-heap for larger half)
- **Time**: O(log n) per insertion, O(1) median retrieval

## Memory Layout:

### Array Representation:
```
Heap: [50, 30, 40, 10, 20, 35, 25]
Tree:      50
          /  \
        30    40
       / \   / \
      10 20 35 25
```

### Advantages:
- **No pointers**: Memory efficient
- **Cache friendly**: Sequential access patterns
- **Simple indexing**: Mathematical relationships

### Disadvantages:
- **Fixed size**: Array needs resizing for dynamic heaps
- **No arbitrary access**: Can't efficiently access middle elements

## Heap vs Other Structures:

### vs Binary Search Tree:
- **Heap**: Weaker ordering, O(1) min/max, O(log n) search
- **BST**: Strong ordering, O(log n) min/max, O(log n) search
- **Use heap for**: Priority queue operations
- **Use BST for**: General searching and ordering

### vs Sorted Array:
- **Heap**: O(log n) insert, O(1) min/max
- **Sorted Array**: O(n) insert, O(1) min/max
- **Use heap for**: Dynamic insertion/deletion
- **Use sorted array for**: Static data with frequent min/max queries

## Implementation Tips:

### Language Considerations:
- **Python**: `heapq` module (min-heap only)
- **Java**: `PriorityQueue` class
- **C++**: `priority_queue` (max-heap default)
- **JavaScript**: No built-in heap, need custom implementation

### Common Pitfalls:
1. **Forgetting heap property**: Not maintaining parent-child relationship
2. **Off-by-one errors**: Array indexing calculations
3. **Max vs Min**: Confusing which type of heap you need
4. **Stability**: Heap sort is not stable

### Optimization Techniques:
- **Bottom-up heapify**: O(n) heap construction
- **Ternary heaps**: Better constant factors for some operations
- **Lazy deletion**: Mark deleted rather than actually removing
