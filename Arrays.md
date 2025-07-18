# Arrays

## What is it?
A collection of elements stored in contiguous memory locations, accessible by index.

## Key Characteristics:
- **Fixed size** (in most languages)
- **O(1) access time** by index
- **Homogeneous** elements (same data type)
- **Zero-based indexing** in most languages

## Time Complexity:
- Access: O(1)
- Search: O(n)
- Insertion: O(n) - need to shift elements
- Deletion: O(n) - need to shift elements

## When to Use:
- When you need fast access to elements by index
- When the size is known and relatively fixed
- Mathematical operations and algorithms
- Building blocks for other data structures

## Example Use Cases:
- Storing pixel data in images
- Implementing matrices for mathematical computations
- Buffer for streaming data

## Memory Layout:
- Elements stored in contiguous memory blocks
- Cache-friendly due to spatial locality
- Predictable memory access patterns

## Variants:
1. **Static Arrays**: Fixed size at compile time
2. **Dynamic Arrays**: Resizable (ArrayList, Vector, Array in JS)
3. **Multi-dimensional Arrays**: Arrays of arrays (matrices)

## Common Operations:
- **Traversal**: Visit each element O(n)
- **Binary Search**: O(log n) on sorted arrays
- **Sorting**: Various algorithms (QuickSort, MergeSort)
- **Rotation**: Shifting elements left/right

## Implementation Notes:
- Most languages provide built-in array support
- Memory allocation is typically handled by the runtime
- Bounds checking varies by language (C/C++ vs Java/Python)

## Visual Examples

### Array Structure and Memory Layout

#### Basic Array Representation:
```
Array: [10, 20, 30, 40, 50]
Index:  0   1   2   3   4

Memory Layout (conceptual):
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴─────┴─────┴─────┘
Address: 1000  1004  1008  1012  1016
         (assuming 4 bytes per integer)
```

#### Zero-Based Indexing:
```
Array: ['A', 'B', 'C', 'D', 'E']
        ↑    ↑    ↑    ↑    ↑
Index:  0    1    2    3    4

To access element 'C': array[2]
To access last element: array[4] or array[length-1]
```

### Array Operations Visualized

#### 1. Array Access - O(1)
```
Array: [10, 20, 30, 40, 50]
       
Access array[2]:
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴──▲──┴─────┴─────┘
              Direct access
              Result: 30
```

#### 2. Array Search - O(n)
```
Linear search for value 40:

Step 1: Check index 0
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└──▲──┴─────┴─────┴─────┴─────┘
   ❌ (10 ≠ 40)

Step 2: Check index 1
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴──▲──┴─────┴─────┴─────┘
         ❌ (20 ≠ 40)

Step 3: Check index 2
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴──▲──┴─────┴─────┘
               ❌ (30 ≠ 40)

Step 4: Check index 3
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴─────┴──▲──┴─────┘
                     ✅ Found!
```

#### 3. Array Insertion - O(n)
```
Insert 25 at index 2:

Original:
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴─────┴─────┴─────┘

Step 1: Shift elements right
┌─────┬─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │     │ 30  │ 40  │ 50  │
└─────┴─────┴─────┴─────┴─────┴─────┘
                   ───→  ───→  ───→

Step 2: Insert new element
┌─────┬─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 25  │ 30  │ 40  │ 50  │
└─────┴─────┴─────┴─────┴─────┴─────┘
```

#### 4. Array Deletion - O(n)
```
Delete element at index 2 (value 30):

Original:
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴─▲───┴─────┴─────┘
              Delete this

Step 1: Remove element
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │     │ 40  │ 50  │
└─────┴─────┴─────┴─────┴─────┘

Step 2: Shift elements left
┌─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 40  │ 50  │
└─────┴─────┴─────┴─────┘
              ←───  ←───
```

### Multi-dimensional Arrays

#### 2D Array (Matrix):
```
2D Array: matrix[3][4]

   Col: 0   1   2   3
Row 0: [1] [2] [3] [4]
Row 1: [5] [6] [7] [8]
Row 2: [9][10][11][12]

Memory Layout (Row-major order):
┌───┬───┬───┬───┬───┬───┬───┬───┬───┬────┬────┬────┐
│ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │ 11 │ 12 │
└───┴───┴───┴───┴───┴───┴───┴───┴───┴────┴────┴────┘
  Row 0 elements    Row 1 elements    Row 2 elements

Access matrix[1][2]: 
- Calculate: 1 * 4 + 2 = 6th position
- Result: 7
```

#### 3D Array:
```
3D Array: cube[2][3][2]

Layer 0:          Layer 1:
[1] [2]          [7] [8]
[3] [4]          [9] [10]
[5] [6]          [11][12]

Visualization:
    Layer 0              Layer 1
    ┌─────┬─────┐       ┌─────┬─────┐
    │  1  │  2  │       │  7  │  8  │
    ├─────┼─────┤       ├─────┼─────┤
    │  3  │  4  │       │  9  │ 10  │
    ├─────┼─────┤       ├─────┼─────┤
    │  5  │  6  │       │ 11  │ 12  │
    └─────┴─────┘       └─────┴─────┘
```

### Array vs. Other Data Structures

#### Array vs. Linked List:
```
Array (Contiguous Memory):
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴─────┴─────┴─────┘
  ↑ Direct access via index

Linked List (Non-contiguous Memory):
┌─────┬──┐    ┌─────┬──┐    ┌─────┬──┐    ┌─────┬──┐    ┌─────┬──┐
│ 10  │ ●┼───→│ 20  │ ●┼───→│ 30  │ ●┼───→│ 40  │ ●┼───→│ 50  │ ∅│
└─────┴──┘    └─────┴──┘    └─────┴──┘    └─────┴──┘    └─────┴──┘
  ↑ Must traverse from head
```

### Cache Performance Visualization

#### Good Cache Locality (Arrays):
```
Sequential Access Pattern:
Memory: [A][B][C][D][E][F][G][H]
Cache:  [A][B][C][D] ← Cache line loads 4 elements
        
Access A: Cache miss, load cache line
Access B: Cache hit ✓
Access C: Cache hit ✓  
Access D: Cache hit ✓
```

#### Poor Cache Locality (Random Access):
```
Random Access Pattern:
Memory: [A][B][C][D][E][F][G][H]
        
Access A: Cache miss, load [A][B][C][D]
Access G: Cache miss, load [E][F][G][H]
Access B: Cache hit ✓
Access H: Cache hit ✓
```

### Dynamic Array Growth

#### ArrayList/Vector Growth Pattern:
```
Initial capacity: 4
┌─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │
└─────┴─────┴─────┴─────┘

Add element 50 (capacity exceeded):
Step 1: Create new array (double size)
┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
│     │     │     │     │     │     │     │     │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘

Step 2: Copy existing elements
┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │     │     │     │     │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘

Step 3: Add new element
┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │     │     │     │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘
```

### Common Array Algorithms Visualized

#### Binary Search (on sorted array):
```
Sorted Array: [10, 20, 30, 40, 50, 60, 70, 80]
Search for: 50

Step 1: Check middle (index 3)
┌────┬────┬────┬────┬────┬────┬────┬────┐
│ 10 │ 20 │ 30 │ 40 │ 50 │ 60 │ 70 │ 80 │
└────┴────┴────┴─▲──┴────┴────┴────┴────┘
                  40 < 50, search right

Step 2: Check middle of right half (index 5)
┌────┬────┬────┬────┬────┬────┬────┬────┐
│ 10 │ 20 │ 30 │ 40 │ 50 │ 60 │ 70 │ 80 │
└────┴────┴────┴────┴────┴─▲──┴────┴────┘
                           60 > 50, search left

Step 3: Check index 4
┌────┬────┬────┬────┬────┬────┬────┬────┐
│ 10 │ 20 │ 30 │ 40 │ 50 │ 60 │ 70 │ 80 │
└────┴────┴────┴────┴─▲──┴────┴────┴────┘
                      Found! 50 = 50
```

#### Array Rotation:
```
Original: [1, 2, 3, 4, 5]
Rotate right by 2 positions:

Step 1: Take last 2 elements
┌───┬───┬───┬───┬───┐
│ 1 │ 2 │ 3 │ 4 │ 5 │
└───┴───┴───┴─▲─┴─▲─┘
              Take these

Step 2: Shift remaining elements right
┌───┬───┬───┬───┬───┐
│   │   │ 1 │ 2 │ 3 │
└───┴───┴───┴───┴───┘

Step 3: Place taken elements at beginning
┌───┬───┬───┬───┬───┐
│ 4 │ 5 │ 1 │ 2 │ 3 │
└───┴───┴───┴───┴───┘
```

## Real-World Examples

### Image Processing:
```
Grayscale Image (2D Array):
pixel[y][x] represents intensity (0-255)

     x: 0   1   2   3   4
y=0:   [255][200][150][100][50 ]
y=1:   [200][180][120][80 ][30 ]
y=2:   [150][130][100][60 ][20 ]
y=3:   [100][90 ][70 ][40 ][10 ]

Visual representation:
█████ ████  ███   ██    █
████  ████  ██    █     
███   ███   ██    █     
██    ██    █         
```

### Matrix Operations:
```
Matrix Addition:
A + B = C

    [1  2]     [5  6]     [6  8 ]
    [3  4]  +  [7  8]  =  [10 12]

Element-wise: C[i][j] = A[i][j] + B[i][j]
```
