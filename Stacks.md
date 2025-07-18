# Stacks

## What is it?
A Last-In-First-Out (LIFO) data structure where elements are added and removed from the same end (top).

## Core Operations:
- **Push**: Add element to top
- **Pop**: Remove element from top
- **Peek/Top**: View top element without removing
- **isEmpty**: Check if stack is empty

## Time Complexity:
- Push: O(1)
- Pop: O(1)
- Peek: O(1)
- Search: O(n)

## When to Use:
- Function call management
- Expression evaluation and syntax parsing
- Undo operations
- Backtracking algorithms

## Example Use Cases:
- Browser back button
- Function call stack in programming
- Balanced parentheses checking
- Depth-First Search (DFS)

## Implementation Approaches:
1. **Array-based**: Fixed or dynamic array with top pointer
2. **Linked List-based**: Singly linked list with head as top

## Stack Applications in Detail:

### Function Call Stack:
- Each function call creates a new stack frame
- Contains local variables, parameters, return address
- Automatic cleanup when function returns
- Stack overflow occurs when too many nested calls

### Expression Evaluation:
- **Infix to Postfix**: Convert using operator stack
- **Postfix Evaluation**: Use operand stack
- **Bracket Matching**: Track opening/closing pairs

### Backtracking Algorithms:
- Maze solving
- N-Queens problem
- Sudoku solving
- Tree/graph traversal with path tracking

## Memory Management:
- Stack memory is automatically managed
- LIFO nature enables efficient allocation/deallocation
- Stack overflow protection in most systems
- Faster than heap allocation

## Variants:
- **Min/Max Stack**: Track minimum/maximum element
- **Monotonic Stack**: Maintain elements in sorted order
- **Stack with Middle**: Support middle element operations
