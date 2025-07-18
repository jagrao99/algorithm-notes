# Sets

## What is it?
A collection of unique elements with no duplicates, supporting set operations like union, intersection, and difference.

## Types:
1. **Hash Set**: Using hash table implementation
2. **Tree Set**: Using balanced tree implementation
3. **Bit Set**: Using bit arrays for integer sets

## Time Complexity (Hash Set - Average):
- Insert: O(1)
- Delete: O(1)
- Search: O(1)
- Union/Intersection: O(n)

## When to Use:
- Removing duplicates
- Membership testing
- Set operations (union, intersection)
- Mathematical set theory applications

## Example Use Cases:
- Removing duplicates from data
- Checking membership in a group
- Finding common elements between datasets
- Implementing mathematical set operations

## Set Operations:

### Basic Operations:
- **Add**: Insert element (no duplicates)
- **Remove**: Delete element if present
- **Contains**: Check if element exists
- **Size**: Number of elements
- **Clear**: Remove all elements

### Set Theory Operations:
- **Union (A ∪ B)**: All elements in A or B
- **Intersection (A ∩ B)**: Elements in both A and B
- **Difference (A - B)**: Elements in A but not in B
- **Symmetric Difference (A ⊕ B)**: Elements in A or B but not both
- **Subset**: Check if A ⊆ B
- **Superset**: Check if A ⊇ B

## Implementation Approaches:

### Hash Set:
- **Underlying structure**: Hash table
- **Average performance**: O(1) for basic operations
- **Worst case**: O(n) if many collisions
- **Memory**: Moderate overhead for hash table
- **Order**: No guaranteed iteration order

### Tree Set (Sorted Set):
- **Underlying structure**: Self-balancing BST (Red-Black, AVL)
- **Performance**: O(log n) for basic operations
- **Memory**: Pointer overhead for tree nodes
- **Order**: Elements maintained in sorted order
- **Additional operations**: Range queries, first/last element

### Bit Set:
- **Underlying structure**: Array of bits
- **Performance**: O(1) for operations, O(n/w) for set operations
- **Memory**: Very efficient for dense integer sets
- **Limitation**: Only works for non-negative integers in known range
- **Bitwise operations**: Very fast union/intersection using bit operations

## Set Applications:

### Data Deduplication:
```
Input: [1, 2, 2, 3, 3, 3, 4]
Set: {1, 2, 3, 4}
Output: [1, 2, 3, 4]
```

### Membership Testing:
- **Access Control**: Check if user has permission
- **Blacklisting**: Check if IP/domain is blocked
- **Feature Flags**: Check if feature is enabled

### Mathematical Operations:
- **Venn Diagrams**: Visualize set relationships
- **Database Joins**: Set intersection for inner joins
- **Recommendation Systems**: Find common interests

## Language-Specific Implementations:

### Python:
```python
# Hash set
s = set([1, 2, 3])
s.add(4)
s.remove(2)

# Set operations
a = {1, 2, 3}
b = {3, 4, 5}
union = a | b        # {1, 2, 3, 4, 5}
intersection = a & b  # {3}
difference = a - b    # {1, 2}
```

### Java:
```java
// Hash set
Set<Integer> hashSet = new HashSet<>();

// Tree set (sorted)
Set<Integer> treeSet = new TreeSet<>();

// Operations
hashSet.add(1);
boolean exists = hashSet.contains(1);
hashSet.remove(1);
```

### JavaScript:
```javascript
// ES6 Set
const s = new Set([1, 2, 3]);
s.add(4);
s.delete(2);
s.has(3); // true

// Set operations (manual implementation needed)
const union = new Set([...a, ...b]);
const intersection = new Set([...a].filter(x => b.has(x)));
```

## Advanced Set Concepts:

### Multiset (Bag):
- **Allows duplicates**: Elements can appear multiple times
- **Count tracking**: Maintains frequency of each element
- **Operations**: Modified to handle counts
- **Use cases**: Frequency analysis, histogram data

### Fuzzy Sets:
- **Partial membership**: Elements have membership degrees [0,1]
- **Applications**: Machine learning, approximate matching
- **Operations**: Modified using fuzzy logic

### Disjoint Set Union (Union-Find):
- **Purpose**: Track connected components
- **Operations**: Union, Find with path compression
- **Applications**: Kruskal's MST, connectivity problems

## Performance Considerations:

### Hash Set vs Tree Set:
| Operation | Hash Set | Tree Set |
|-----------|----------|----------|
| Add/Remove | O(1) avg | O(log n) |
| Contains | O(1) avg | O(log n) |
| Iteration | O(n) | O(n) |
| Min/Max | O(n) | O(1) |
| Range Query | Not supported | O(log n) |

### Memory Usage:
- **Hash Set**: Hash table overhead (~2x element size)
- **Tree Set**: Pointer overhead (~3x element size)
- **Bit Set**: 1 bit per possible element (very efficient for dense sets)

### Cache Performance:
- **Hash Set**: Good locality for small sets
- **Tree Set**: Poor locality due to tree traversal
- **Bit Set**: Excellent locality for bitwise operations

## Common Use Cases:

### Algorithm Problems:
- **Two Sum**: Use set to check if complement exists
- **Finding Duplicates**: Add to set, check if already present
- **Intersection of Arrays**: Convert to sets, find intersection

### System Design:
- **Caching**: Track cached items
- **Rate Limiting**: Track recent requests
- **Distributed Systems**: Membership in clusters

### Data Processing:
- **ETL Pipelines**: Remove duplicate records
- **Data Validation**: Check against valid value sets
- **Analytics**: Unique visitor counting

## Implementation Tips:

### Choosing the Right Set:
- **Hash Set**: Default choice for uniqueness and fast lookup
- **Tree Set**: When you need sorted order or range operations
- **Bit Set**: For dense integer sets with known bounds

### Custom Equality:
- **Hash Sets**: Require proper hashCode() and equals()
- **Tree Sets**: Require proper compareTo() or Comparator
- **Immutable keys**: Ensure set elements don't change after insertion

### Performance Optimization:
- **Initial capacity**: Set appropriate size for hash sets
- **Load factor**: Tune for hash set performance
- **Bulk operations**: Use addAll(), retainAll() for set operations
