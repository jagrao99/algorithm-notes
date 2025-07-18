# Queues

## What is it?
A First-In-First-Out (FIFO) data structure where elements are added at one end (rear) and removed from the other end (front).

## Types:
1. **Simple Queue**: Basic FIFO
2. **Circular Queue**: Last position connects to first
3. **Priority Queue**: Elements have priorities
4. **Deque (Double-ended queue)**: Insert/delete from both ends

## Core Operations:
- **Enqueue**: Add element to rear
- **Dequeue**: Remove element from front
- **Front**: View front element
- **isEmpty**: Check if queue is empty

## Time Complexity:
- Enqueue: O(1)
- Dequeue: O(1)
- Search: O(n)

## When to Use:
- Process scheduling in operating systems
- Breadth-First Search (BFS)
- Handling requests in web servers
- Print job management

## Example Use Cases:
- CPU task scheduling
- Breadth-First Search traversal
- Handling asynchronous requests
- Buffer for data streams

## Implementation Approaches:

### Array-based Implementation:
- **Simple Array**: Inefficient due to shifting
- **Circular Array**: Efficient with front/rear pointers
- **Dynamic Array**: Resize when needed

### Linked List Implementation:
- **Two Pointers**: Front and rear references
- **Advantages**: Dynamic size, no shifting
- **Disadvantages**: Extra memory for pointers

## Circular Queue Details:
- **Advantage**: Reuse empty spaces efficiently
- **Full Condition**: `(rear + 1) % size == front`
- **Empty Condition**: `front == rear`
- **Size Calculation**: `(rear - front + size) % size`

## Priority Queue:
- Elements have associated priorities
- Higher priority elements dequeued first
- Implementation: Heap, sorted array, or BST
- Applications: Task scheduling, Dijkstra's algorithm

## Deque (Double-ended Queue):
- **Operations**: AddFront, AddRear, RemoveFront, RemoveRear
- **Implementation**: Circular array or doubly linked list
- **Use Cases**: Sliding window problems, palindrome checking

## Queue Applications:

### Operating Systems:
- **Process Scheduling**: Ready queue, waiting queue
- **I/O Buffers**: Keyboard, disk, network buffers
- **Print Spooling**: Manage print jobs in order

### Algorithms:
- **BFS**: Level-order tree traversal
- **Graph Algorithms**: Shortest path in unweighted graphs
- **Cache Implementation**: LRU with queue + hash table

### Real-time Systems:
- **Producer-Consumer**: Buffer between processes
- **Streaming Data**: Audio/video processing
- **Network Packets**: Router queues
