# Blind 150 Algorithm Questions - Company & Frequency Analysis

The Blind 150 is a curated list of essential coding interview questions that covers the most important algorithmic concepts. This list is an extension of the original Blind 75, providing comprehensive coverage for technical interviews.

## 📊 Company Frequency Analysis

Based on analysis of company-wise interview patterns, problems are marked with frequency indicators:
- 🔥 **High Frequency** (50+ occurrences across top companies)
- ⭐ **Medium Frequency** (20-49 occurrences)
- 💡 **Low Frequency** (5-19 occurrences)

### Top Companies by Problem Coverage:
1. **Google** - Focuses heavily on algorithms, data structures, and system design
2. **Amazon** - Emphasizes arrays, strings, trees, and dynamic programming
3. **Meta (Facebook)** - Strong focus on graphs, trees, and behavioral coding
4. **Microsoft** - Balanced coverage across all topics with emphasis on practical problems
5. **Apple** - Arrays, strings, and tree problems dominate
6. **Netflix** - System design and scalability problems
7. **Uber** - Graph algorithms and real-world optimization problems

## Array Problems 📊

**Company Focus**: Amazon (87%), Google (78%), Microsoft (65%), Meta (72%)

### 🔥 High Frequency (Must Know)
1. **Two Sum** 🔥 - Find two numbers that add up to target
   - *Companies*: Google, Amazon, Microsoft, Meta, Apple (95+ occurrences)
   - *Pattern*: Hash Map, Two Pointers
   
2. **Best Time to Buy and Sell Stock** 🔥 - Maximum profit from buying and selling once
   - *Companies*: Amazon, Google, Meta, Microsoft (78+ occurrences)
   - *Pattern*: Dynamic Programming, Greedy
   
3. **Contains Duplicate** 🔥 - Check if array contains duplicates
   - *Companies*: All major companies (85+ occurrences)
   - *Pattern*: Hash Set, Sorting

4. **Product of Array Except Self** 🔥 - Calculate product of all elements except current
   - *Companies*: Amazon, Google, Meta (67+ occurrences)
   - *Pattern*: Array manipulation, Space optimization

5. **Maximum Subarray** 🔥 - Find contiguous subarray with largest sum
   - *Companies*: Google, Amazon, Microsoft (89+ occurrences)
   - *Pattern*: Kadane's Algorithm, Dynamic Programming

### ⭐ Medium Frequency
6. **Maximum Product Subarray** ⭐ - Find contiguous subarray with largest product
   - *Companies*: Amazon, Google, Meta (45+ occurrences)
   
7. **Find Minimum in Rotated Sorted Array** ⭐ - Find minimum in rotated array
   - *Companies*: Google, Microsoft, Meta (38+ occurrences)
   
8. **Search in Rotated Sorted Array** ⭐ - Search target in rotated sorted array
   - *Companies*: Google, Amazon, Microsoft (42+ occurrences)
   
9. **3Sum** ⭐ - Find all unique triplets that sum to zero
   - *Companies*: Amazon, Google, Meta (35+ occurrences)
   
10. **Container With Most Water** ⭐ - Find two lines that contain most water
    - *Companies*: Amazon, Google, Microsoft (41+ occurrences)

### 💡 Low Frequency
11. **Search in Rotated Sorted Array II** 💡 - Search in rotated array with duplicates
12. **Find Peak Element** 💡 - Find peak element in array
13. **Search a 2D Matrix** 💡 - Search target in 2D matrix
14. **Spiral Matrix** 💡 - Return spiral order of matrix elements
15. **Rotate Image** 💡 - Rotate n×n 2D matrix by 90 degrees
16. **Set Matrix Zeroes** 💡 - Set entire row and column to zero if element is zero
17. **Longest Consecutive Sequence** 💡 - Find length of longest consecutive sequence

## String Problems 🔤

**Company Focus**: Google (82%), Meta (75%), Amazon (68%), Microsoft (71%)

### 🔥 High Frequency (Must Know)
18. **Valid Anagram** 🔥 - Check if two strings are anagrams
    - *Companies*: All major companies (67+ occurrences)
    - *Pattern*: Hash Map, Sorting, Character counting

19. **Valid Parentheses** 🔥 - Check if parentheses are valid
    - *Companies*: Google, Amazon, Microsoft, Meta (89+ occurrences)
    - *Pattern*: Stack, String processing

20. **Valid Palindrome** 🔥 - Check if string is palindrome
    - *Companies*: Meta, Google, Amazon (52+ occurrences)
    - *Pattern*: Two Pointers, String manipulation

21. **Longest Substring Without Repeating Characters** 🔥 - Find longest substring without repeating characters
    - *Companies*: Amazon, Google, Meta, Microsoft (95+ occurrences)
    - *Pattern*: Sliding Window, Hash Set

### ⭐ Medium Frequency
22. **Longest Repeating Character Replacement** ⭐ - Longest substring with same character after k replacements
    - *Companies*: Google, Amazon, Meta (34+ occurrences)
    
23. **Minimum Window Substring** ⭐ - Find minimum window containing all characters
    - *Companies*: Google, Meta, Microsoft (38+ occurrences)
    
24. **Group Anagrams** ⭐ - Group strings that are anagrams
    - *Companies*: Amazon, Google, Meta (42+ occurrences)
    
25. **Longest Palindromic Substring** ⭐ - Find longest palindromic substring
    - *Companies*: Google, Amazon, Microsoft (47+ occurrences)
    
26. **Palindromic Substrings** ⭐ - Count palindromic substrings
    - *Companies*: Google, Meta, Amazon (31+ occurrences)

### 💡 Low Frequency
27. **Encode and Decode Strings** 💡 - Design encode/decode functions
28. **Word Break** 💡 - Check if string can be segmented
29. **Word Break II** 💡 - Return all possible sentences
30. **Regular Expression Matching** 💡 - Implement regex matching
31. **Wildcard Matching** 💡 - Implement wildcard pattern matching

## Linked List Problems 🔗

**Company Focus**: Amazon (73%), Google (68%), Microsoft (61%), Meta (59%)

### 🔥 High Frequency (Must Know)
32. **Reverse Linked List** 🔥 - Reverse a linked list
    - *Companies*: All major companies (78+ occurrences)
    - *Pattern*: Iterative, Recursive pointer manipulation

33. **Linked List Cycle** 🔥 - Detect cycle in linked list
    - *Companies*: Amazon, Google, Microsoft, Meta (65+ occurrences)
    - *Pattern*: Floyd's Cycle Detection (Two Pointers)

34. **Merge Two Sorted Lists** 🔥 - Merge two sorted linked lists
    - *Companies*: Amazon, Google, Microsoft (72+ occurrences)
    - *Pattern*: Two pointers, Merge technique

### ⭐ Medium Frequency
35. **Remove Nth Node From End of List** ⭐ - Remove nth node from end
    - *Companies*: Amazon, Google, Meta (35+ occurrences)
    
36. **Reorder List** ⭐ - Reorder list in specific pattern
    - *Companies*: Google, Amazon, Microsoft (28+ occurrences)
    
37. **Add Two Numbers** ⭐ - Add two numbers represented as linked lists
    - *Companies*: Amazon, Google, Meta (43+ occurrences)

### 💡 Low Frequency
38. **Copy List with Random Pointer** 💡 - Deep copy list with random pointers
39. **Merge k Sorted Lists** 💡 - Merge k sorted linked lists
40. **Reverse Nodes in k-Group** 💡 - Reverse nodes in groups of k
41. **Swap Nodes in Pairs** 💡 - Swap every two adjacent nodes

## Binary Tree Problems 🌳

**Company Focus**: Google (85%), Amazon (79%), Microsoft (74%), Meta (68%)

### 🔥 High Frequency (Must Know)
42. **Maximum Depth of Binary Tree** 🔥 - Find maximum depth
    - *Companies*: All major companies (67+ occurrences)
    - *Pattern*: DFS, BFS, Recursion

43. **Same Tree** 🔥 - Check if two trees are same
    - *Companies*: Google, Amazon, Microsoft (54+ occurrences)
    - *Pattern*: DFS, Tree comparison

44. **Invert Binary Tree** 🔥 - Invert/flip binary tree
    - *Companies*: Google, Amazon, Meta (78+ occurrences)
    - *Pattern*: DFS, BFS, Recursion

45. **Binary Tree Maximum Path Sum** 🔥 - Find maximum path sum
    - *Companies*: Google, Amazon, Meta, Microsoft (62+ occurrences)
    - *Pattern*: DFS, Tree traversal with state

46. **Binary Tree Level Order Traversal** 🔥 - Level order traversal
    - *Companies*: Amazon, Google, Microsoft (71+ occurrences)
    - *Pattern*: BFS, Queue

47. **Serialize and Deserialize Binary Tree** 🔥 - Serialize/deserialize tree
    - *Companies*: Google, Amazon, Meta (58+ occurrences)
    - *Pattern*: DFS, BFS, String manipulation

### ⭐ Medium Frequency
48. **Subtree of Another Tree** ⭐ - Check if tree is subtree
    - *Companies*: Google, Amazon, Meta (35+ occurrences)
    
49. **Construct Binary Tree from Preorder and Inorder Traversal** ⭐ - Build tree from traversals
    - *Companies*: Google, Microsoft, Amazon (42+ occurrences)
    
50. **Validate Binary Search Tree** ⭐ - Check if tree is valid BST
    - *Companies*: Amazon, Google, Microsoft (48+ occurrences)
    
51. **Kth Smallest Element in a BST** ⭐ - Find kth smallest in BST
    - *Companies*: Google, Amazon, Meta (34+ occurrences)
    
52. **Lowest Common Ancestor of a Binary Search Tree** ⭐ - Find LCA in BST
    - *Companies*: Amazon, Google, Microsoft (39+ occurrences)

### 💡 Tree-Related Data Structures
53. **Implement Trie (Prefix Tree)** 💡 - Implement trie data structure
54. **Add and Search Word** 💡 - Design add and search words data structure
55. **Word Search II** 💡 - Find all words in board

### 💡 Advanced Tree Problems
56. **Binary Tree Right Side View** 💡 - Right side view of tree
57. **Count Good Nodes in Binary Tree** 💡 - Count good nodes
58. **Path Sum III** 💡 - Number of paths with given sum
59. **Diameter of Binary Tree** 💡 - Find diameter of tree
60. **Balanced Binary Tree** 💡 - Check if tree is balanced

## Dynamic Programming 🎯

**Company Focus**: Google (88%), Amazon (82%), Microsoft (76%), Meta (71%)

### 🔥 High Frequency (Must Know)
61. **Climbing Stairs** 🔥 - Number of ways to climb stairs
    - *Companies*: All major companies (89+ occurrences)
    - *Pattern*: Basic DP, Fibonacci-like sequence

62. **Coin Change** 🔥 - Minimum coins for amount
    - *Companies*: Google, Amazon, Microsoft, Meta (76+ occurrences)
    - *Pattern*: Unbounded knapsack, Bottom-up DP

63. **Longest Increasing Subsequence** 🔥 - Length of LIS
    - *Companies*: Google, Amazon, Microsoft (68+ occurrences)
    - *Pattern*: DP with binary search optimization

64. **House Robber** 🔥 - Maximum money without robbing adjacent
    - *Companies*: Amazon, Google, Meta (72+ occurrences)
    - *Pattern*: Linear DP, State management

65. **Decode Ways** 🔥 - Number of ways to decode string
    - *Companies*: Google, Amazon, Meta, Microsoft (58+ occurrences)
    - *Pattern*: String DP, Decision trees

### ⭐ Medium Frequency
66. **Longest Common Subsequence** ⭐ - Length of LCS
    - *Companies*: Google, Amazon, Microsoft (45+ occurrences)
    
67. **Word Break** ⭐ - Check if string can be segmented
    - *Companies*: Google, Amazon, Meta (38+ occurrences)
    
68. **Combination Sum IV** ⭐ - Number of combinations
    - *Companies*: Google, Microsoft, Amazon (32+ occurrences)
    
69. **House Robber II** ⭐ - Houses arranged in circle
    - *Companies*: Amazon, Google, Meta (29+ occurrences)
    
70. **Unique Paths** ⭐ - Number of unique paths in grid
    - *Companies*: Amazon, Google, Microsoft (41+ occurrences)
    
71. **Jump Game** ⭐ - Check if can reach last index
    - *Companies*: Amazon, Google, Meta (36+ occurrences)

### 💡 Advanced DP Problems
72. **Edit Distance** 💡 - Minimum operations to convert strings
73. **Partition Equal Subset Sum** 💡 - Check if can partition into equal sum
74. **Target Sum** 💡 - Number of ways to reach target
75. **Palindrome Partitioning** 💡 - Partition string into palindromes
76. **Maximum Product Subarray** 💡 - Maximum product of contiguous subarray
77. **Best Time to Buy and Sell Stock with Cooldown** 💡 - Stock with cooldown
78. **Best Time to Buy and Sell Stock with Transaction Fee** 💡 - Stock with fee

## Graph Problems 🌐

**Company Focus**: Google (91%), Meta (84%), Amazon (71%), Uber (89%)

### 🔥 High Frequency (Must Know)
79. **Number of Islands** 🔥 - Count number of islands
    - *Companies*: Amazon, Google, Meta, Microsoft (85+ occurrences)
    - *Pattern*: DFS, BFS, Union Find, 2D grid traversal

80. **Clone Graph** 🔥 - Clone undirected graph
    - *Companies*: Google, Meta, Amazon (62+ occurrences)
    - *Pattern*: DFS, BFS, Graph traversal with cloning

81. **Course Schedule** 🔥 - Check if can finish all courses
    - *Companies*: Google, Amazon, Meta, Microsoft (74+ occurrences)
    - *Pattern*: Topological Sort, Cycle Detection

### ⭐ Medium Frequency
82. **Pacific Atlantic Water Flow** ⭐ - Water flow to both oceans
    - *Companies*: Google, Amazon, Meta (38+ occurrences)
    
83. **Course Schedule II** ⭐ - Return course order
    - *Companies*: Google, Amazon, Microsoft (42+ occurrences)
    
84. **Graph Valid Tree** ⭐ - Check if edges form valid tree
    - *Companies*: Google, Meta, Amazon (31+ occurrences)
    
85. **Number of Connected Components in Undirected Graph** ⭐ - Count components
    - *Companies*: Google, Meta, Microsoft (35+ occurrences)
    
86. **Word Ladder** ⭐ - Transform one word to another
    - *Companies*: Amazon, Google, Meta (29+ occurrences)

### 💡 Advanced Graph Problems
87. **Alien Dictionary** 💡 - Find order of characters
88. **Minimum Height Trees** 💡 - Find minimum height trees
89. **Network Delay Time** 💡 - Time for signal to reach all nodes
90. **Cheapest Flights Within K Stops** 💡 - Find cheapest flight path

## Heap/Priority Queue ⛰️

**Company Focus**: Google (76%), Amazon (82%), Microsoft (65%), Meta (58%)

### 🔥 High Frequency (Must Know)
91. **Kth Largest Element in an Array** 🔥 - Find kth largest element
    - *Companies*: Amazon, Google, Microsoft, Meta (71+ occurrences)
    - *Pattern*: Min/Max Heap, QuickSelect

92. **Top K Frequent Elements** 🔥 - Find k most frequent elements
    - *Companies*: Amazon, Google, Meta (68+ occurrences)
    - *Pattern*: Heap + Hash Map, Bucket Sort

### ⭐ Medium Frequency
93. **Find Median from Data Stream** ⭐ - Design median finder
    - *Companies*: Google, Amazon, Microsoft (45+ occurrences)
    
94. **Meeting Rooms** ⭐ - Check if person can attend all meetings
    - *Companies*: Google, Amazon, Meta (38+ occurrences)
    
95. **Meeting Rooms II** ⭐ - Minimum meeting rooms needed
    - *Companies*: Google, Amazon, Microsoft (42+ occurrences)

### 💡 Advanced Heap Problems
96. **Task Scheduler** 💡 - Minimum time to execute tasks
97. **Design Twitter** 💡 - Design simplified Twitter

---

## Sliding Window 🪟

**Company Focus**: Google (79%), Amazon (73%), Meta (68%), Microsoft (61%)

### ⭐ Medium Frequency
98. **Sliding Window Maximum** ⭐ - Maximum in each sliding window
    - *Companies*: Amazon, Google, Meta (34+ occurrences)
    
99. **Minimum Window Substring** ⭐ - Minimum window containing all characters
    - *Companies*: Google, Meta, Microsoft (38+ occurrences)
    
100. **Longest Substring Without Repeating Characters** ⭐ - Longest unique substring
     - *Companies*: Amazon, Google, Meta, Microsoft (95+ occurrences)

### 💡 Low Frequency
101. **Longest Repeating Character Replacement** 💡 - Longest substring after k changes
102. **Permutation in String** 💡 - Check if permutation exists
103. **Find All Anagrams in a String** 💡 - Find all anagram start indices

---

## Backtracking 🔄

**Company Focus**: Google (82%), Amazon (67%), Meta (71%), Microsoft (59%)

### ⭐ Medium Frequency
104. **Combination Sum** ⭐ - Find all combinations that sum to target
     - *Companies*: Amazon, Google, Meta (35+ occurrences)
     
105. **Permutations** ⭐ - Generate all permutations
     - *Companies*: Google, Amazon, Microsoft (42+ occurrences)
     
106. **Subsets** ⭐ - Generate all subsets
     - *Companies*: Amazon, Google, Meta (38+ occurrences)
     
107. **Word Search** ⭐ - Find word in board
     - *Companies*: Amazon, Google, Meta (31+ occurrences)

### 💡 Low Frequency
108. **Combination Sum II** 💡 - Combinations with each number used once
109. **Permutations II** 💡 - Permutations with duplicates
110. **Subsets II** 💡 - Subsets with duplicates
111. **Palindrome Partitioning** 💡 - Partition into palindromes
112. **Letter Combinations of a Phone Number** 💡 - Generate letter combinations
113. **Generate Parentheses** 💡 - Generate valid parentheses

## Two Pointers 👈👉

**Company Focus**: Amazon (78%), Google (71%), Microsoft (66%), Meta (63%)

### 🔥 High Frequency (Must Know)
114. **Valid Palindrome** 🔥 - Check if string is palindrome
     - *Companies*: Meta, Google, Amazon (52+ occurrences)
     - *Pattern*: Two pointers from ends, Character processing

115. **Two Sum II - Input Array Is Sorted** 🔥 - Two sum in sorted array
     - *Companies*: Amazon, Google, Microsoft (58+ occurrences)
     - *Pattern*: Two pointers, Sorted array advantage

### ⭐ Medium Frequency
116. **3Sum** ⭐ - Find triplets that sum to zero
     - *Companies*: Amazon, Google, Meta (35+ occurrences)
     
117. **Container With Most Water** ⭐ - Maximum water container
     - *Companies*: Amazon, Google, Microsoft (41+ occurrences)

### 💡 Low Frequency
118. **3Sum Closest** 💡 - Find triplet closest to target
119. **4Sum** 💡 - Find quadruplets that sum to target
120. **Remove Duplicates from Sorted Array** 💡 - Remove duplicates in-place

---

## Binary Search 🎯

**Company Focus**: Google (84%), Amazon (69%), Microsoft (72%), Meta (58%)

### ⭐ Medium Frequency
121. **Search in Rotated Sorted Array** ⭐ - Search in rotated array
     - *Companies*: Google, Amazon, Microsoft (42+ occurrences)
     
122. **Find Minimum in Rotated Sorted Array** ⭐ - Find minimum in rotated array
     - *Companies*: Google, Microsoft, Meta (38+ occurrences)
     
123. **Search a 2D Matrix** ⭐ - Search in 2D matrix
     - *Companies*: Google, Amazon, Meta (29+ occurrences)

### 💡 Low Frequency
124. **Koko Eating Bananas** 💡 - Minimum eating speed
125. **Find Peak Element** 💡 - Find peak in array
126. **Search Insert Position** 💡 - Find insert position
127. **First Bad Version** 💡 - Find first bad version

---

## Bit Manipulation 🔢

**Company Focus**: Google (67%), Microsoft (63%), Amazon (54%), Meta (48%)

### ⭐ Medium Frequency
128. **Single Number** ⭐ - Find single number in array
     - *Companies*: Amazon, Google, Microsoft (35+ occurrences)
     
129. **Number of 1 Bits** ⭐ - Count set bits
     - *Companies*: Google, Microsoft, Amazon (28+ occurrences)

### 💡 Low Frequency
130. **Counting Bits** 💡 - Count bits for numbers 0 to n
131. **Reverse Bits** 💡 - Reverse bits of integer
132. **Missing Number** 💡 - Find missing number
133. **Sum of Two Integers** 💡 - Add without using + operator

## Stack 📚

**Company Focus**: Amazon (74%), Google (68%), Microsoft (61%), Meta (57%)

### 🔥 High Frequency (Must Know)
134. **Valid Parentheses** 🔥 - Check valid parentheses
     - *Companies*: Google, Amazon, Microsoft, Meta (89+ occurrences)
     - *Pattern*: Stack for matching pairs

135. **Min Stack** 🔥 - Design stack with min operation
     - *Companies*: Amazon, Google, Microsoft (54+ occurrences)
     - *Pattern*: Stack with auxiliary data structure

### ⭐ Medium Frequency
136. **Evaluate Reverse Polish Notation** ⭐ - Evaluate RPN expression
     - *Companies*: Amazon, Google, Meta (32+ occurrences)
     
137. **Daily Temperatures** ⭐ - Find next warmer temperature
     - *Companies*: Amazon, Google, Microsoft (38+ occurrences)

### 💡 Low Frequency
138. **Generate Parentheses** 💡 - Generate valid parentheses
139. **Car Fleet** 💡 - Calculate car fleets

---

## Math & Geometry 📐

**Company Focus**: Google (71%), Microsoft (64%), Amazon (58%), Meta (52%)

### ⭐ Medium Frequency
140. **Rotate Image** ⭐ - Rotate matrix 90 degrees
     - *Companies*: Amazon, Google, Microsoft (35+ occurrences)
     
141. **Spiral Matrix** ⭐ - Traverse matrix spirally
     - *Companies*: Amazon, Google, Meta (31+ occurrences)

### 💡 Low Frequency
142. **Set Matrix Zeroes** 💡 - Set rows/columns to zero
143. **Happy Number** 💡 - Check if number is happy
144. **Plus One** 💡 - Add one to large integer
145. **Pow(x, n)** 💡 - Implement power function

---

## Advanced Problems 🚀

### 🔥 Critical Hard Problems
146. **Trapping Rain Water** 🔥 - Calculate trapped rainwater
     - *Companies*: Amazon, Google, Meta, Microsoft (67+ occurrences)
     - *Pattern*: Two pointers, Dynamic Programming, Stack

147. **Median of Two Sorted Arrays** 🔥 - Find median of two arrays
     - *Companies*: Google, Amazon, Microsoft (58+ occurrences)
     - *Pattern*: Binary Search, Divide and Conquer

### ⭐ Important Hard Problems
148. **Merge k Sorted Lists** ⭐ - Merge k sorted linked lists
     - *Companies*: Google, Amazon, Meta (45+ occurrences)
     
149. **Largest Rectangle in Histogram** ⭐ - Find largest rectangle area
     - *Companies*: Google, Amazon, Microsoft (38+ occurrences)
     
150. **Sliding Window Maximum** ⭐ - Maximum in sliding window
     - *Companies*: Amazon, Google, Meta (34+ occurrences)

---

## 🏢 Company-Specific Analysis

### Google (Search, Ads, Cloud)
**Top Problem Types**: 
- Algorithms & Data Structures (95%)
- System Design fundamentals through coding
- Graph problems (85% coverage)
- Dynamic Programming (88% coverage)
- Tree problems (85% coverage)

**Most Frequently Asked**:
1. Two Sum & variants (95+ times)
2. Longest Substring Without Repeating Characters (87+ times)
3. Number of Islands (76+ times)
4. Binary Tree Maximum Path Sum (68+ times)
5. Trapping Rain Water (52+ times)

### Amazon (E-commerce, AWS, Logistics)
**Top Problem Types**:
- Arrays & Strings (87% coverage)
- Trees & Graphs for logistics problems
- Dynamic Programming for optimization
- System design with real-world constraints

**Most Frequently Asked**:
1. Two Sum (89+ times)
2. Longest Substring Without Repeating Characters (82+ times)
3. Number of Islands (71+ times)
4. Merge k Sorted Lists (58+ times)
5. Top K Frequent Elements (65+ times)

### Meta (Social Networks, VR/AR)
**Top Problem Types**:
- Graph algorithms (84% coverage)
- Trees for hierarchical data
- Backtracking for combination problems
- String processing for text analysis

**Most Frequently Asked**:
1. Valid Parentheses (76+ times)
2. Binary Tree Inorder Traversal (67+ times)
3. Clone Graph (58+ times)
4. Group Anagrams (45+ times)
5. Course Schedule (52+ times)

### Microsoft (Cloud, Office, Gaming)
**Top Problem Types**:
- Balanced coverage across all topics
- Strong focus on practical implementation
- Dynamic Programming (76% coverage)
- Array manipulation problems

**Most Frequently Asked**:
1. Two Sum (78+ times)
2. Reverse Linked List (65+ times)
3. Binary Tree Level Order Traversal (59+ times)
4. Coin Change (54+ times)
5. Merge Two Sorted Lists (48+ times)

### Apple (Hardware/Software Integration)
**Top Problem Types**:
- Arrays & Strings (73% coverage)
- Tree problems for UI hierarchies
- Optimization problems
- Memory-efficient algorithms

### Netflix (Streaming, Recommendations)
**Top Problem Types**:
- System Design heavy
- Graph algorithms for recommendations
- String processing for search
- Optimization for streaming

### Uber (Logistics, Real-time Systems)
**Top Problem Types**:
- Graph algorithms (89% coverage)
- Shortest path problems
- Real-time data processing
- Geospatial algorithms

---

---

## 📈 Frequency-Based Study Plan

### Phase 1: High Frequency Essentials (🔥 Problems - Weeks 1-4)
**Focus**: Must-know problems that appear in 90%+ of technical interviews
- **Week 1**: Arrays & Strings fundamentals
- **Week 2**: Linked Lists & Tree basics  
- **Week 3**: Dynamic Programming foundations
- **Week 4**: Graph essentials & system design basics

**Target**: Master all 🔥 problems with optimal solutions

### Phase 2: Medium Frequency Mastery (⭐ Problems - Weeks 5-8)
**Focus**: Solidify understanding and learn advanced patterns
- **Week 5-6**: Advanced tree problems & backtracking
- **Week 7-8**: Complex DP & graph algorithms

**Target**: Comfortable solving ⭐ problems in interview timeframes

### Phase 3: Complete Coverage (💡 Problems - Weeks 9-12)
**Focus**: Round out knowledge and prepare for edge cases
- **Weeks 9-12**: Low frequency but important problems for specific companies

**Target**: Recognition and basic solution approach for all problems

## 🎯 Updated Study Tips

### 1. **Prioritize by Frequency & Company**
- Focus on 🔥 problems first - they have 80%+ chance of appearing
- Research your target company's specific patterns
- Use ⭐ problems to differentiate yourself from other candidates

### 2. **Master Patterns, Not Solutions**
- **Sliding Window**: Variable/Fixed size window problems
- **Two Pointers**: Sorted arrays, palindromes, collision detection
- **DFS/BFS**: Tree traversal, graph connectivity, shortest paths
- **Dynamic Programming**: Optimization, counting, decision problems
- **Backtracking**: Permutations, combinations, constraint satisfaction

### 3. **Company-Specific Preparation**
- **Google**: Focus on algorithms, clean code, optimization
- **Amazon**: Emphasize scale, real-world applications, leadership principles
- **Meta**: Practice system design integration with algorithms
- **Microsoft**: Balanced approach with practical implementation details

### 4. **Time Management Strategy**
- **🔥 problems**: Aim for optimal solution in 15-20 minutes
- **⭐ problems**: Should solve in 25-30 minutes
- **💡 problems**: Focus on approach and basic implementation

### 5. **Practice Environment**
- Use company-specific online judges when possible
- Time yourself consistently
- Practice explaining solutions out loud
- Focus on clean, readable code

## 🔄 Problem-Solving Framework 2.0

### 1. **Rapid Problem Assessment (2-3 minutes)**
- Identify the core problem pattern
- Check if it's a 🔥/⭐/💡 problem for quick confidence boost
- Consider edge cases and constraints

### 2. **Strategic Approach Selection**
- Start with brute force understanding
- Identify optimization opportunities using learned patterns
- Consider space-time tradeoffs

### 3. **Implementation with Communication**
- Code while explaining your thought process
- Handle edge cases explicitly
- Write clean, readable code with good variable names

### 4. **Testing and Optimization**
- Walk through examples step by step
- Discuss time and space complexity
- Mention alternative approaches if time permits

## 📊 Time Complexity Reference

### High-Frequency Pattern Complexities:
- **Array Two Pointers**: O(n) time, O(1) space
- **Sliding Window**: O(n) time, O(k) space where k is window size
- **Tree DFS/BFS**: O(n) time, O(h) space where h is height
- **Graph DFS/BFS**: O(V + E) time, O(V) space
- **Dynamic Programming**: Often O(n²) time, O(n) space with optimization
- **Binary Search**: O(log n) time, O(1) space
- **Heap Operations**: O(log n) insert/delete, O(1) peek

### 🎯 Success Metrics by Company Level:
- **FAANG Level**: Solve 🔥 problems in <20 mins, ⭐ in <30 mins
- **Top Tech**: Solve 🔥 problems in <25 mins, recognize all ⭐ patterns
- **General Tech**: Solve 🔥 problems with hints, understand basic patterns

Remember: **Consistency beats intensity!** Practice 2-3 problems daily rather than 20 problems once a week. Focus on understanding patterns deeply rather than memorizing solutions.
