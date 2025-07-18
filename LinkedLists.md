# Linked Lists

## What is it?
A linear data structure where elements (nodes) are stored in sequence, with each node containing data and a reference/pointer to the next node.

## Types:
1. **Singly Linked List**: Each node points to the next
2. **Doubly Linked List**: Each node has pointers to both next and previous
3. **Circular Linked List**: Last node points back to the first

## Time Complexity:
- Access: O(n)
- Search: O(n)
- Insertion: O(1) if you have the reference, O(n) if searching
- Deletion: O(1) if you have the reference, O(n) if searching

## When to Use:
- When you need frequent insertions/deletions
- When the size varies significantly
- When you don't need random access to elements
- Implementing other data structures (stacks, queues)

## Example Use Cases:
- Undo functionality in applications
- Music playlist (next/previous songs)
- Browser history navigation

## Node Structure:
```
Singly Linked Node:
[Data | Next] -> [Data | Next] -> [Data | NULL]

Doubly Linked Node:
NULL <- [Prev | Data | Next] <-> [Prev | Data | Next] -> NULL
```

## Advantages:
- Dynamic size
- Efficient insertion/deletion at beginning
- Memory allocated as needed
- No memory waste (unlike arrays with unused slots)

## Disadvantages:
- No random access (must traverse from head)
- Extra memory overhead for pointers
- Not cache-friendly due to non-contiguous memory
- No backward traversal (singly linked)

## Common Operations:
- **Traversal**: Visit each node O(n)
- **Insertion**: At beginning O(1), at end O(n), at position O(n)
- **Deletion**: By value O(n), by reference O(1)
- **Reversal**: Change direction of pointers O(n)

## Memory Considerations:
- Each node requires extra memory for pointer(s)
- Nodes can be scattered throughout memory
- Garbage collection complexity in managed languages
