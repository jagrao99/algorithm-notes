# Hash Tables (Hash Maps)

## What is it?
A data structure that maps keys to values using a hash function to compute an index into an array of buckets or slots. Think of it as a super-fast lookup table where you can find any value instantly if you know its key.

## How It Works:
1. **Hash Function**: Converts any key into an array index
2. **Bucket Array**: Stores the actual key-value pairs
3. **Collision Resolution**: Handles when multiple keys hash to the same index
4. **Load Factor**: Ratio of stored elements to array size (affects performance)

## Key Characteristics:
- **Key-value pairs**: Store associated data
- **Hash function** converts keys to array indices
- **Collision handling** (chaining, open addressing)
- **Dynamic sizing** in most implementations
- **No guaranteed order** of elements

## Hash Functions

### Properties of Good Hash Functions:
1. **Deterministic**: Same input always produces same output
2. **Uniform Distribution**: Spreads keys evenly across array
3. **Fast Computation**: Should be O(1)
4. **Avalanche Effect**: Small input changes cause large output changes

### Common Hash Function Techniques:
```
Division Method: hash(key) = key % table_size
Multiplication Method: hash(key) = floor(table_size * (key * A % 1))
Universal Hashing: Randomly chosen from family of hash functions
```

## Collision Resolution Strategies

### 1. Separate Chaining (Closed Addressing)
- Each bucket contains a linked list of elements
- Multiple elements can exist at same index
- **Pros**: Simple, handles high load factors well
- **Cons**: Extra memory for pointers, cache performance

### 2. Open Addressing (Closed Hashing)
Elements stored directly in the array, find next available slot when collision occurs.

**Linear Probing**: 
- Check next slot: `(hash(key) + i) % table_size`
- **Pros**: Good cache performance, simple
- **Cons**: Clustering problems

**Quadratic Probing**: 
- Check slots: `(hash(key) + i²) % table_size`
- **Pros**: Reduces clustering
- **Cons**: May not find empty slot even if available

**Double Hashing**: 
- Use second hash function: `(hash1(key) + i * hash2(key)) % table_size`
- **Pros**: Excellent distribution
- **Cons**: More complex, requires good second hash function

## Load Factor and Resizing

### Load Factor (α):
```
α = number of elements / table size
```

### Critical Thresholds:
- **Separate Chaining**: Performance degrades when α > 1.0
- **Open Addressing**: Performance degrades when α > 0.7
- **Optimal Range**: Usually keep α between 0.5 - 0.75

### Dynamic Resizing:
1. **When to Resize**: Load factor exceeds threshold
2. **How to Resize**: Create new table (usually 2x size)
3. **Rehashing**: Move all elements to new table using new hash function
4. **Cost**: O(n) operation, but amortized O(1) per insertion

## Time Complexity Analysis

### Average Case (Good Hash Function, Proper Load Factor):
- **Search**: O(1)
- **Insert**: O(1)
- **Delete**: O(1)
- **Space**: O(n)

### Worst Case (Poor Hash Function, All Collisions):
- **Search**: O(n)
- **Insert**: O(n)
- **Delete**: O(n)

### Best Case:
- All operations: O(1) with no collisions

## Implementation Considerations

### Choosing Table Size:
- **Prime Numbers**: Often preferred to reduce clustering
- **Powers of 2**: Faster modulo operation (bit masking)
- **Initial Size**: Start with reasonable size based on expected data

### Key Design Decisions:
1. **Hash Function Selection**: Balance speed vs. distribution quality
2. **Collision Resolution**: Chaining vs. open addressing
3. **Load Factor Threshold**: When to trigger resize
4. **Growth Strategy**: How much to grow (typically 2x)

## Advanced Variations

### 1. Robin Hood Hashing
- Variant of open addressing
- Minimize variance in probe distances
- "Rich" elements give way to "poor" ones

### 2. Cuckoo Hashing
- Guarantees O(1) worst-case lookup
- Uses two hash functions and two tables
- May require rehashing entire table

### 3. Consistent Hashing
- Used in distributed systems
- Minimizes rehashing when nodes added/removed
- Key for scalable distributed hash tables

## Memory Layout and Cache Performance

### Cache Considerations:
- **Separate Chaining**: Poor cache locality due to pointer chasing
- **Open Addressing**: Better cache locality, sequential memory access
- **Memory Overhead**: Chaining has pointer overhead, open addressing has empty slots

## Practical Implementation Tips

### Language-Specific Notes:
- **Python**: `dict` uses open addressing with random probing
- **Java**: `HashMap` uses separate chaining with red-black trees for large buckets
- **C++**: `std::unordered_map` typically uses separate chaining
- **JavaScript**: Objects and Maps use different internal implementations

### Common Pitfalls:
1. **Poor Hash Function**: Can destroy O(1) performance
2. **Not Handling Resize**: Fixed-size tables degrade with growth
3. **Ignoring Load Factor**: High load factors kill performance
4. **Key Mutability**: Changing keys after insertion breaks the structure

## Real-World Applications

### Database Systems:
- **Hash Indexes**: Fast equality lookups
- **Join Operations**: Hash joins for large datasets
- **Query Optimization**: Symbol tables for query planning

### Programming Language Implementations:
- **Symbol Tables**: Variable/function name resolution
- **String Interning**: Reduce memory usage for duplicate strings
- **Method Dispatch**: Virtual function table lookups

### Web Development:
- **Session Management**: User session storage
- **Caching Layers**: Redis, Memcached implementations
- **URL Routing**: Mapping URLs to handlers

### System Software:
- **Memory Management**: Page table implementations
- **File Systems**: Directory structure lookups
- **Network Protocols**: ARP tables, routing tables

## When to Use Hash Tables:
- **Fast lookups by key** are critical
- **Key uniqueness** is guaranteed or desired
- **Order doesn't matter** for your use case
- **Memory is available** for good load factors
- **Keys are hashable** (immutable, comparable)

## When NOT to Use Hash Tables:
- **Order matters** (use ordered maps or arrays)
- **Range queries** needed (use trees)
- **Memory is extremely constrained**
- **Keys are not hashable**
- **Predictable worst-case performance** required

## Performance Benchmarking Example:
```
Operation Count: 1,000,000 elements
Hash Table (good hash): ~1-2ms average lookup
Binary Search Tree: ~20ms average lookup  
Linear Search Array: ~500ms average lookup
```

## Interview Questions to Master:
1. How do you handle collisions in a hash table?
2. What happens when a hash table gets too full?
3. How would you implement a hash table from scratch?
4. Why might hash table performance degrade?
5. Design a hash function for strings.
6. How does load factor affect performance?
